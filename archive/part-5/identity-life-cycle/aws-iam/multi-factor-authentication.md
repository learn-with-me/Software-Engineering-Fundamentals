# Multi-Factor Authentication \(MFA\)

#### Steps to setup

* Sign in to the AWS Management Console and open the IAM console at https://console.aws.amazon.com/iam/home?region=us-east-1\#/security\_credentials
* Choose the **AWS IAM credentials** tab. Next to **Assigned MFA device**, choose **Assign MFA Device**.
* In the **Manage MFA Device** wizard, choose **Virtual MFA device**, and then choose **Continue**.
  * IAM generates and displays configuration information for the virtual MFA device, including a QR code graphic. The graphic is a representation of the "secret configuration key" that is available for manual entry on devices that do not support QR codes.
* Open your favorite virtual MFA app \(available in PlayStore or AppStore\). Examples:
  * Google Authenticator
  * Duo Mobile
* Determine whether the MFA app supports QR codes, and then do one of the following:
  * From the wizard, choose **Show QR code**, and then use the app to scan the QR code. For example, you might choose the camera icon or choose an option similar to **Scan code**, and then use the device's camera to scan the code.
  * In the **Manage MFA Device** wizard, choose **Show secret key**, and then type the secret key into your MFA app.
  * When you are finished, the virtual MFA device starts generating one-time passwords.
* In the **Manage MFA Device** wizard, in the **MFA code 1** box, type the one-time password that currently appears in the virtual MFA device. Wait up to 30 seconds for the device to generate a new one-time password. Then type the second one-time password into the **MFA code 2** box. Choose **Assign MFA**.



