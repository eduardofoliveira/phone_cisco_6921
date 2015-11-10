I have used configuration the same as in foloving sites:

https://github.com/amooma/GS3/wiki/Cisco-CP-69xx-VoIP-Telefone-mit-Asterisk-Gemeinschaft
https://zadarma.com/ru/support/instructions/cisco/cisco-6921/

But I need configure some custom settings. For example

1) I used g729a codec and I need callStats for correct end calls

\<preferredCodec>g729a\</preferredCodec>

\<callStats>false\</callStats>

2) Set messageWaitingLampPolicy to 3

How the phone alerts the user to unread voicemail messages.

The messageWaitingLampPolicy values work like this:

 - Primary Line - Light and Prompt set to 1
 - Primary Line - Prompt Only set to 2
 - Primary Line - Light Only set to 3
 - Light and Prompt presumably set to 4
 - Prompt Only presumably set to 5
 - Light Only presumably set to 6
 - None set to 7

Light Lamp and Display Prompt if message is waiting - 3

'Light' is the bright red lamp on the headset

'Prompt' will show up a flashing voicemail envelope next to the Line on the RHS side of the display when there is voicemail

3) I need set amount of calls phone can recive simultaneously. Otherwise it set response busy when have more then one calls

\<maxNumCalls>4\</maxNumCalls>

\<busyTrigger>2\</busyTrigger>

 - maxNumCalls — Defines the maximum number of calls allowed per line.
 - busyTrigger — Defines the number of calls that triggers Call Forward Busy per line on the SIP phone.

4) Configure 2-nd line with auto answer

<autoAnswerTimer>1</autoAnswerTimer>

\<line button="2">

\<autoAnswerEnabled>3\</autoAnswerEnabled>

\<autoAnswerMode>Auto Answer with Speakerphone\</autoAnswerMode>

 - autoAnswerEnabled - 3 - enable auto answer
 - autoAnswerTimer - Seconds to wait before automatically answering the call for lines with <autoAnswerEnabled /> set to 1. Set to 10 sec - 3 calls

5) Configure access

\<sshAccess>1\</sshAccess>

\<webAccess>1\</webAccess>

\<settingsAccess>2\</settingsAccess>

 - sshAccess - 1 - disabled. For enable set 0
 - webAccess - 1 - disabled. For enable set 0
 - settingsAccess - Enables and disables the Settings button on an IP phone.
   0 = Disabled.
   1 = Enabled (default). The phone user can modify features by using the Settings menu.
   2 = Restricted. The phone user is allowed to access User Preferences and volume settings only. 

