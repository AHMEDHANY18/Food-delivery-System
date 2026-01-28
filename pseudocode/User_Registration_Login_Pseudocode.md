========================================
User Registration & Login – Pseudocode
========================================


1. User Registration
----------------------------------------
BEGIN UserRegistration

INPUT userData (name, email, password, phone)

IF userData is invalid THEN
    RETURN "Validation Error"
END IF

IF email already exists in database THEN
    RETURN "User Already Exists"
END IF

hashedPassword = HASH(password)

CREATE newUser WITH
    name,
    email,
    hashedPassword,
    status = INACTIVE

ASSIGN defaultRole TO newUser

CREATE cart FOR newUser

GENERATE verificationCode (Email / OTP)

SEND verificationCode TO user

IF verificationCode is NOT verified THEN
    RETURN "Account Verification Failed"
END IF

UPDATE newUser status TO ACTIVE

RETURN "Registration Successful"

END UserRegistration


2. User Login
----------------------------------------
BEGIN UserLogin

INPUT email, password

IF email OR password is empty THEN
    RETURN "Invalid Credentials"
END IF

user = FIND user BY email

IF user does NOT exist THEN
    RETURN "User Not Found"
END IF

IF password does NOT match user.hashedPassword THEN
    RETURN "Invalid Credentials"
END IF

IF user.status != ACTIVE THEN
    SEND verificationCode TO user
    RETURN "Account Not Verified"
END IF

LOAD userRoles AND userPermissions

GENERATE authToken

RETURN authToken, "Login Successful"

END UserLogin


3. Email / OTP Verification
----------------------------------------
BEGIN VerifyAccount

INPUT userId, verificationCode

storedCode = GET verificationCode FROM database

IF verificationCode != storedCode THEN
    RETURN "Invalid Verification Code"
END IF

UPDATE user status TO ACTIVE

DELETE verificationCode

RETURN "Account Verified Successfully"

END VerifyAccount


4. Forgot Password
----------------------------------------
BEGIN ForgotPassword

INPUT email

user = FIND user BY email

IF user does NOT exist THEN
    RETURN "User Not Found"
END IF

GENERATE resetToken

SEND resetToken TO user email

IF resetToken is NOT verified THEN
    RETURN "Password Reset Failed"
END IF

INPUT newPassword

hashedPassword = HASH(newPassword)

UPDATE user password WITH hashedPassword

RETURN "Password Reset Successful"

END ForgotPassword


5. Logout
----------------------------------------
BEGIN Logout

INPUT authToken

INVALIDATE authToken

CLEAR user session

RETURN "Logout Successful"

END Logout


========================================
End of Pseudocode
========================================
