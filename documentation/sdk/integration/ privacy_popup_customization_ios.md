# Privacy consents popup
There are two configurations for Privacy popup, Default and Media, you can also customize it as you prefer.

1. [Default](#default)
2. [Media configuration](#media-configuration)
3. [Custom configuration](#custom-configuration)

## Default

Please select this option for a partnership model "data only". By default, privacy popup screen appears as shown in the following screenshots:
<br><br>
<img src="http://www.geouniq.com/images/default_ios_1.png" width="20%">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;
<img src="http://www.geouniq.com/images/default_ios_2.png" width="20%">
<br><br>

This is the default text:
```
The location data we collect allows us to optimize your user experience. By clicking "accept", you consent to share your position with our partners.
Our partners collect and process only de-identified data for analytics and ad targeting purposes exclusively from users who have consented to location 
data sharing. You can change your data sharing preferences at any time by accessing your settings or by contacting our partners.
By proceeding you confirm that you are over 16 and that you have read both our privacy policy and Geouniq's privacy policy.
```
Languages available: English, Italian, French.

## Media configuration
For a partnership model "media", add the following key and value to Info.plist file (Number Type) 

```
GuConsentsPopupStyle: 1
```
<br><br>
<img src="http://www.geouniq.com/images/media_ios_1.png" width="20%">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;
<img src="http://www.geouniq.com/images/media_ios_2.png" width="20%">
<br><br>

This is the media text:
```
The location data we collect allows us to optimize your user experience. By clicking "accept", you consent to share your position with our partners.
Our partners collect and process only de-identified data for analytics and ad targeting purposes exclusively from users who have consented to location
data sharing. If you do not accept, advertisement will still appear however not based on your interests. 
You can change your data sharing preferences at any time by accessing your settings or by contacting our partners. 
By proceeding you confirm that you are over 16 and that you have read both our privacy policy and Geouniq's privacy policy.
```
Languages available: English, Italian, French.

## Custom configuration 

You can customize privacy and consents views.<br>
You can customize the desired elements by adding the respective keys to Info.plist

### To customize Privacy view:

|   Key   |   Type   |    Description      |
|---|---|---|
|GuPrivacyTitle|String|Title|
|GuPrivacySubtitle|String|Subtitle|
|GuPrivacyBody|String|Body|
|GuPrivacyTermUrl|String|Url of Privacy Term|
|GuPrivacyAcceptTextColor|String|Text color of button "Accept" according with format: #ffffff|
|GuPrivacyBackgroundColor|String|Background view color according with format: #ffffff|
|GuPrivacyAcceptBackgroundColor|String|Background color of button "Accept" according with format: #ffffff|
|GuPrivacyTextColor|String|Text color (all except the button Acccept) according with format: #ffffff|

### To customize Consent view:

|   Key   |   Type   |    Description      |
|---|---|---|
|GuConsentTitle|String|Title|
|GuConsentSubtitle|String|Subtitle|
|GuConsentSaveBackgroundColor|String|Background color of button "Save" according with format: #ffffff|
|GuConsentSaveTextColor|String|Text color of button "Save" according with format: #ffffff|
|GuConsentBackgroundColor|String|Background view color according with format: #ffffff|
|GuConsentTextColor|String|Text color (all except the button "Save") according with format: #ffffff|
|GuConsentSwitchColor|String|Switch color according with format: #ffffff|



### To customize image inside views:

To change the image inside the views, add an image named `GuPrivacyAndConsentImage` to the project (the image can be added as a file or within xcassets)

