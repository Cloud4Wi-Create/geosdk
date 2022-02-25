# Privacy consents popup

There are two configurations for Privacy popup, Default and Media, you can also customize it as you prefer. 

1. [Default](#default)
2. [Media configuration](#media-configuration)
3. [Custom configuration](#custom-configuration)

## Default

Please select this option for a partnership model "data only".
By default, privacy screen and consents screen appears as shown in the following screenshot:

<br>

<img src="https://www.geouniq.com/images/privacy_screen_android.png" width="20%">
&nbsp;&nbsp;&nbsp;&nbsp;
<img src="https://www.geouniq.com/images/privacy_consents_screen_android.png" width="20%">

<br>
<br>

This is the default text:
```
The location data we collect allows us to optimize your user experience. By clicking "accept", you consent to share your position with our partners. 
Our partners collect and process only de-identified data for analytics and ad targeting purposes exclusively from users who have consented to location data sharing.
You can change your data preferences using the link below. You can withdraw your consent at any time by accessing your settings or by contacting our partners. 
By proceeding you confirm that you are over 16 and that you have read both our privacy policy and Geouniq'sprivacy policy.
```
Languages available: English, Italian, French.

## Media configuration
For a partnership model "media", you must declare in your app a new style in styles.xml, as shown below:
```xml
<style name="PrivacyPolicyViewStyle">
    <item name="privacySubtitle">@string/privacy_policy_advertising_subtitle</item>
    <item name="privacyBody">@string/privacy_policy_advertising_body</item>
</style>
```
This is the media text:
```
The location data we collect allows us to optimize your user experience. By clicking “accept”, you consent to share your position with our partners.
Our partners collect and process only de-identified data for analytics and ad targeting purposes exclusively from users who have consented to location data sharing.
You can change your data preferences using the link below. You can withdraw your consent at any time by accessing your settings or by contacting our partners.
If you do not accept, advertisement will still appear however not based on your interests.
By proceeding you confirm that you are over 16 and that you have read both our privacy policy and Geouniq's privacy policy.
```
Languages available: English, Italian, French.

## Custom configuration 

You can customize privacy and consenst views by declaring in your app these new styles in styles.xml, as shown below.
You can use a localized string resource if you want a localized message in the popup.
> you must define only the attributes that you need to customize, the other ones remain with the default appearance

For privacy screen:
```xml
 <style name="PrivacyPolicyViewStyle">
    <item name="privacyLogoSrc">@drawable/your_customized_logo</item>
    <item name="privacyTitle">@string/your_customized_title</item>
    <item name="privacySubtitle">@string/your_customized_subtitle</item>
    <item name="privacyBody">@string/your_customized_body</item>
    <item name="privacyPolicyLink">@string/your_customized_privacy_link</item>
    <item name="privacyTextColor">@color/your_customized_text_color</item>
    <item name="privacyViewBackground">@color/your_customized_background_color</item>
    <item name="privacyAcceptButtonBackground">@color/your_customized_accept_button_background_color</item>
    <item name="privacyAcceptButtonTextColor">@color/your_customized_accept_button_text_color</item>
</style>
```

For consents screen:
```xml
<style name="ConsentsViewStyle">
    <item name="consentsLogoSrc">@drawable/your_customized_privacy_policy_logo</item>
    <item name="consentsTitle">@string/your_customized_consents_title</item>
    <item name="consentsSubtitle">@string/your_customized_consents_subtitle</item>
    <item name="colorControlActivated">@color/your_customized_switch_color_when_active</item>
    <item name="consentsTextColor">@color/your_customized_text_color</item>
    <item name="consentsViewBackground">@color/your_customized_background_color</item>
    <item name="consentsAcceptButtonBackground">@color/your_customized_accept_button_background_color</item>
    <item name="consentsAcceptButtonTextColor">@color/your_customized_accept_button_text_color</item>
</style>
```