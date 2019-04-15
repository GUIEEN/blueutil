https://plugable.com/2016/06/22/understanding-bluetooth-wireless-audio/

Before the start of the millennium, the cellular mobile phone was relatively new. Laptops were large and heavy, the PDA (Personal Digital Assistant for the uninitiated) was just about to arrive on the scene, and the Apple Newton was about the closest thing there was to a smartphone.

Bluetooth wireless technology was conceived in this era when a group of visionary engineers realized that using wires to connect devices to those new wireless mobile phones would limit their usability and adoption. They wanted something that didn’t exist: a wireless connection that was low power and inexpensive, yet robust enough for the variety of uses they had envisioned. In particular, they understood that both data and audio connections were being enabled by the cellular networks that provided these mobile phone connections.

The rest is history. The initial Bluetooth specification came out in 2000 and new hardware quickly followed. The audio headset became the killer device for Bluetooth, becoming so successful that the term Bluetooth became the term popularly used for a wireless headset (“where did I leave my Bluetooth?”)

As often happens with technology, as the platforms expanded so did the use cases. The headset implementation worked well for its initial intended purpose but wasn’t good enough in some scenarios, particularly for higher quality speakers and stereo headsets. To address these new scenarios, different and more advanced encoding methods were being developed and support for these and quality stereo was needed (see Codecs below). These were introduced starting with an enhanced audio channel and eventually a high quality Advanced Audio Profile as discussed below.

The Bluetooth 4.0 specification introduced a lower power, lower data rate technology called Bluetooth low energy (BLE) as discussed in our earlier blog post about Bluetooth wireless technology. While audio is starting to see some applications using BLE, the rest of the discussion for this post will focus on Classic Bluetooth technology, also called BR/EDR (for Basic Rate/Enhanced Data Rate).

Unfortunately, previous versions of devices and software persist in the marketplace, including headsets, phones, cars and computers. This blog post will also unravel the various versions and implementations to help us all understand what to expect from Bluetooth audio devices.

Bluetooth wireless audio
To help understand how Bluetooth audio works, a brief explanation of how sound is represented in the diigitally will be helpful.

How digital sound works
Sound is transferred physically through the air as waves of pressure. Your ear turns these pressure waves into electrical signals that are passed to your brain and you hear the sound.

An analogous method is used in the electronic world to convert audio: sound is converted from pressure waves into electrical signals by a microphone. These signals are electrical waveforms that can be used to alter recording materials such as vinyl records or analog tape. For use in computers and digital electronics like smartphones, these continuous electrical signals are converted to numeric representation by sampling and digitization.

The audio electronic signal is measured (digitized) at very fast time intervals (samples). Each sample is a number representing the amplitude of the signal at the moment the sample is taken. The sequence of samples created in this way forms a digital representation of the sound. This representation can be recorded, transmitted and manipulated by computers using digital signal processing, improving the quality and reducing the amount of data.

Audio digital signal properties
There are several important factors of a digital audio signal, but perhaps the three most important are sampling rate, sample size (number of bits), and compression. These ultimately determine the quality of the digital audio that will be turned back into sound and amount of data required to store or transmit that signal.

Sampling rate
You have probably seen graphical representations of the frequencies in sound. The sampling rate determines what frequencies are possible to record and playback. The faster the sampling rate, the higher the frequencies that can be captured. Typically, the full range of hearing can be reproduced using the frequencies from 20 Hz to 20 KHz. Sound must be sampled at least double the highest frequency present that needs to be reproduced, so you’ll often see sampling rates of 44.1k (twice 20 kHz plus a little extra) samples/second for good music quality.

Acceptable and understandable voice reproduction can be accomplished with significantly lower sampling rates since voice is understandable with just 20 Hz to 4 KHz or sampling of at least 8K samples/second.

Sample size
Numbers are represented in digital communications using bits, and the number of bits per sample determines the number of steps between the softest sounds and loudest sounds that can be recorded, also called the “dynamic range.” For sound, this dynamic range is expressed in decibels or dB. The average human ear can differentiate approximately 90dB of range from the softest sounds to the loudest. Eight bits gives 48dB of range while 16 bits gives 96 dB of range and is therefore the size often used for sampling digital audio.

Compression and Audio codecs
High sampling rates and many bits reproduce the best audio, but they also result in a large amount of data representing that sound.   Digital signal processing is used to compress the data so that it can be stored and transmitted more quickly and using less memory and power.

Compression techniques use algorithms that model sound and compute the difference between the model and the signals, and record only the that difference between the model and the signal. Different models and techniques offer different quality reproduction. Some models worke well for intelligibility of voice while others work better for music.

There are two parts to the sound reproduction, ‘coding’ or using an algorithm and model to reduce the data, and ‘decoding’ which uses algorithms to recover the original signal. Together, these are called CODECs or CODing, DECoding algorithms. An example is the MP3 CODEC that is often used for music distribution. It is also available for use with the Bluetooth A2DP profile discussed later in this article.

Because Bluetooth has strict limitations on bandwidth, MP3 files are often transferred using another CODEC, depending on the requirements and limitations of the particular use and profile.

Data Links
Classic Bluetooth has two types of data channels: Synchronous Communication Oriented links (SCO) for audio, and Asynchronous Communications Links (ACL) for data. Bluetooth BR/EDR technology supports a maximum of 3 SCO links or 7 ACL links or a combination of the two.

This article will focus on the SCO link, but the ACL link can also be used for audio data transfer similarly to VOIP. However, it lacks the guaranteed real-time data provided by the SCO link.

The SCO link guarantees regularly-timed data packets transmitted in reserved time slots no matter how Bluetooth links are used. There is some level of error detection and correction, but there is no retransmission of data and if there are any data drops, those drops can affect the audio. Therefore, the CODEC in use needs to be tolerant of small data losses.

The limitations of the SCO (lack of retransmission and limited CODECs) were addressed in Bluetooth 1.2 with enhanced SCO (eSCO). eSCO allows for retransmission, higher bitrates (up to 288 kb/second as opposed to 64 kb/second) and supports a greater number of higher quality CODECs that use more bandwidth.

In practice, you won’t hear about the SCO or eSCO. Instead devices will just use the best possible link available. For the most part, that will be SCO for headsets and eSCO for stereo audio.

Bluetooth audio profiles
A Bluetooth profile is a set of capabilities provided to support a particular task. Bluetooth audio has developed over time to support additional use cases as they have evolved: from the Headset profile for use with mobile phones to the Hands-Free profile for cars and finally to the Advanced Audio profile for stereo headsets and speakers.

Roles
Although audio is bi-directional, each Bluetooth audio profile has two sides that are not interchangeable since one needs to be in control.

The two roles are called the Audio Gateway (AG), and Headset (HS) or Hands-Free (HF). The AG is typically a phone or computer that is connected to a remote data source. It controls the HS that acts as the remote microphone and speaker and includes commands to answer, hang up, ring, and control the volume.

The two non-interchangeable roles mean that two headsets cannot create a connection like walkie-talkies. Two smartphones could create a local audio connection, but one would have to act like a device and use the HS or HF role instead of acting like a normal AG.

Headset Profile – HSP
The Headset Profile uses the SCO channel and either a CVSD or PCM CODEC that has been tuned to support simple telephone quality voice data. Google these CODECs for more information if you’re interested. They are fascinating to understand, but well outside the scope of this post.

Hands-Free Profile – HFP
The Hands-Free Profile also uses the SCO channel but adds some additional quality by using logarithmic sampling algorithms. It also adds capabilities including last-number redial, call waiting and voice dialing. Most headsets today support HFP as well as HSP, which allows backwards compatibility with older phones and cars.

Both the HSP and HFP are widely used in the standard Bluetooth headsets such as the Plugable Bluetooth Headset BT-HS40B.

Advanced Audio Distribution Profile – A2DP
A2DP uses the eSCO link to provide better quality mono and stereo audio reproduction. It streams high quality audio data in one direction only.

It uses higher quality provided by error correction with retransmission and also provides better quality CODECS such as MP3, AAC, and user-defined CODECs. The main example of a user-defined CODEC in the general market is CSR’s (now Qualcomm’s) aptX®. Note that aptX is not supported on Apple’s products. It is not supported by the Plugable BT-HS40B.

A2DP defines roles a bit differently as Sink (SK) and Source (SC). A music player is a SC and a set of headphones is a SK. Similarly, a microphone is a SC and a recorder is a SK. Some A2DP devices are flexible and can support both roles, although not simultaneously.

Many A2DP-supporting devices also implement HF and HSP for use with bi-directional audio for phone calls and legacy devices. Note that only one of those profiles can be active at a time for each link.

A2DP is used extensively for music listening and for speakers. It uses the improved eSCO channel and better codecs allow for transmission of stereo audio data up to the quality of MP3 sources.

Many Bluetooth stereo headsets also support A2DP for listening to music when they’re not being used for phone calls or as a voice assistant. Only one profile (HFP, HSP, A2DP) can be used at one time. Audio sources like phones work together with headsets to use the appropriate profile depending on the use.

Which profile to use and when
Bluetooth audio provides several use models due to history and technology development. So how and when do you use which profile?

Often this decision is transparent. A phone to a headset will usually choose the best profile supported by the device for phone calls (HFP or HSP). A set of speakers will use the A2DP profile since it will sound much better.

Your car audio system may ask which to use, or allow you to pair twice. If it does, you should go through both processes. This is because the car can be an A2DP SK or it can be a HFP HF device, depending on whether you’re listening to tunes or hands-free talking while driving.

We hope this helps understand the differences between your Bluetooth audio devices and will help you make the best decisions for your audio needs going forward.
