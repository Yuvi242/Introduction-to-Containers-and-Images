# Introduction-to-Containers-and-Images
यह रिपॉजिटरी कंटेनर और इमेज की तकनीकी अवधारणाओं को आसान और सरल शब्दों में समझाने के लिए बनाई गई है।
## Table of Contents
1. [कंटेनर क्या हैं?](#कंटेनर-क्या-हैं)
2. [कंटेनर रनटाइम क्या है?](#कंटेनर-रनटाइम-क्या-है)
3. [कंटेनर रजिस्ट्री क्या है?](#कंटेनर-रजिस्ट्री-क्या-है)
4. [एक कंटेनर इमेज क्या है?](#एक-कंटेनर-इमेज-क्या-है)
5. [एक कंटेनर इमेज कैसे बनाते हैं?](#एक-कंटेनर-इमेज-कैसे-बनाते-हैं)
6. [कंटेनर कैसे चलाते हैं?](#कंटेनर-कैसे-चलाते-हैं)
7. [निष्कर्ष](#निष्कर्ष)

# कंटेनर क्या हैं?

कल्पना करें कि हमलोग पास एक गेम है जो केवल एक ही स्थान पर काम करता है, जैसे कि हमारे कमरे में, क्योंकि इसके लिए बैटरी, उपकरण और शायद गेम से जुड़ी हुई कुछ विशेष वस्तुओं की आवश्यकता होती है। यदि हम इस गेम को अपने मित्र के घर ले जाना चाहते हैं, तो हमें आवश्यक सभी चीजें एक बॉक्स में पैक करनी होंगी, ताकि हमलोग गेम को कहीं भी खेल सकें। कंप्यूटर प्रोग्राम के लिए कंटेनर यही करते हैं\! वे प्रोग्राम को चलाने के लिए आवश्यक हर चीज़ (जैसे कोड, टूल और सेटिंग्स) को एक बॉक्स में पैक करते हैं, ताकि यह किसी भी कंप्यूटर पर काम कर सके, चाहे वह कहीं भी हो।

* कंटेनर हल्के होते हैं और वे ऑपरेटिंग सिस्टम के मुख्य हिस्से को साझा करते हैं, जबकि वर्चुअल मशीनें अपनी खुद की ऑपरेटिंग सिस्टम होती हैं।  
* वे ऐप को अलग कर देते हैं लेकिन वर्चुअल मशीनों की तुलना में कम संसाधनों का उपयोग करते हैं।

**उदाहरण:**  
कल्पना कीजिए कि हमलोग अपने दोस्तों के साथ उनके कंप्यूटर पर नंबर अनुमान करें नाम का एक छोटा गेम खेलना चाहते हैं। हमने पायथन में एक छोटा प्रोग्राम लिखा हैं जो खिलाड़ी को एक संख्या का अनुमान लगाने देता है, और प्रोग्राम उन्हें बताता है कि वे सही हैं या गलत। अब, हमलोग इस गेम को अपने दोस्तों के साथ साझा करना चाहते हैं, इसलिए हमलोग कंटेनर का उपयोग करेंगे ताकि उनके लिए इसे अपने कंप्यूटर पर चलाना आसान हो सके।

# कंटेनर रनटाइम क्या है?

जब हमलोग अपने गेम को एक बॉक्स में पैक करते हैं, तो किसी को बॉक्स खोलने में मदद करने की ज़रूरत होती है और यह सुनिश्चित करना होता है कि अंदर सब कुछ काम करता है। कंटेनर रनटाइम कंटेनरों के लिए यही करता है। कंटेनर रनटाइम एक रोबोट की तरह है जो जानता है कि बॉक्स को कैसे खोलना है और यह सुनिश्चित करना है कि गेम ठीक से काम करे।

किसी भी कंप्यूटर पर अपने गेम (एप्लीकेशन) का उपयोग करने के लिए, हमलोगो को बॉक्स (कंटेनर) खोलने और गेम चलाने के लिए कंटेनर रनटाइम की आवश्यकता होती है।

कंटेनर रनटाइम कंटेनर से संबंधित हर चीज़ का प्रबंधन करता है, जैसे इसे शुरू करना, रोकना और हटाना। OCI (ओपन कंटेनर इनिशिएटिव) मानक के आधार पर कंटेनर शुरू करने के लिए डॉकर runc नामक रनटाइम का उपयोग करता है।

* कंटेनर रनटाइम, जैसे runc, youki या containerd, कंटेनरों को बनाने और चलाने का काम करते हैं।   
* ये रनटाइम यह सुनिश्चित करते हैं कि कंटेनर एक अलग जगह में चले, और सिस्टम के संसाधनों का सही तरीके से उपयोग करें जैसे-  सीपीयू , मेमोरी। 

**उदाहरण:**  
हमलोग डॉकर का इस्तेमाल कर सकते हैं, जो कंटेनरों के लिए एक रोबोट की तरह मदद करता है। हमलोगों ने शायद सुना होगा कि डॉकर कंटेनर शुरू करने के लिए runc नाम की चीज़ का उपयोग करता है। लेकिन इसके बारे में ज्यादा सोचने की जरूरत नहीं है—बस इतना समझ लें कि डॉकर यह सुनिश्चित करता है कि गेम (एप्लीकेशन) कंटेनर के अंदर सही तरीके से चले।

# कंटेनर रजिस्ट्री क्या है?

अब, सोचिये कि हमारे कई दोस्त हैं जो हमारे बनाये इस नंबर अनुमान करें गेम को खेलना चाहते हैं। हर दोस्त को अलग-अलग बॉक्स देने के बजाय, हमलोग उस बॉक्स को एक बड़े स्टोर, जिसे कंटेनर रजिस्ट्री कहते हैं वहां भेज देते हैं, फिर हमारे सारे दोस्त वहां से गेम डाउनलोड कर सकते हैं। कंटेनर रजिस्ट्री कंटेनरों के लिए एक लाइब्रेरी की तरह होती है, जहाँ से सभी उसे ले सकते हैं।

**उदाहरण:**  
असल जिंदगी में, हमलोग अपने गेम को डॉकर हब जैसे एक सार्वजनिक स्टोर में रख सकते हैं, जो एक लोकप्रिय कंटेनर रजिस्ट्री है। फिर हमारे सभी दोस्त डॉकर हब पर जाकर उस गेम को अपने कंप्यूटर पर डाउनलोड कर सकते हैं।

# एक कंटेनर इमेज क्या है?

इससे पहले कि हम अपने गेम को एक डिब्बे में रखें, हमलोग गेम कोड, बैटरी और अन्य ज़रूरी चीज़ों की एक तस्वीर ले लेते हैं। इस तस्वीर को कंटेनर इमेज कहते हैं। कंटेनर इमेज में हमारे प्रोग्राम की सभी ज़रूरी चीजें होती हैं, जो एक डिब्बे (कंटेनर) में पैक करने के लिए तैयार होती हैं।

एक कंटेनर इमेज एक नक्शे या रेसिपी जैसी होती है। इसमें उस एप्लिकेशन को चलाने के लिए सारी ज़रूरी चीजें होती हैं \- जैसे कोड, लाइब्रेरी और सिस्टम की सेटिंग्स। इसे उस प्रोग्राम और उसके काम करने के माहौल की पूरी तस्वीर की तरह समझ सकते हैं।

* हर बार जब कोई कंटेनर शुरू होता है, तो यह उसी पुरानी, बिना बदली हुई इमेज का उपयोग करता है, जब तक हमलोग एक नई इमेज नहीं बनाते।

**उदाहरण :**  
मान लीजिए कि हम अपना संख्या का अनुमान लगाएं गेम पायथन में लिखते हैं। हमने गेम कोड और उसकी ज़रूरत की हर चीज़ की एक तस्वीर (स्नैपशॉट) लेते हैं, और यह हमारे लिए कंटेनर इमेज बन जाती है। बाद में, हमलोग इस इमेज का उपयोग जितने चाहें उतने बॉक्स (कंटेनर) बनाने के लिए कर सकते हैं

# एक कंटेनर इमेज कैसे बनाते हैं?

सोचिए कि हमलोग अपना खिलौना का बॉक्स बनाने जा रहे हैं। सबसे पहले, हमलोग सभी खिलौने, उनके हिस्से, उपकरण और उन्हें इस्तेमाल करने के निर्देश इकट्ठा करते हैं। फिर, हमलोग इन सबको ठीक से बॉक्स में रखते हैं। इसी तरह, कंप्यूटर की दुनिया में हम कंटेनर इमेज बनाते हैं।

एक कंटेनर इमेज बनाने के लिए, हम डॉकरफ़ाइल नाम का एक फाइल बनाते हैं। डॉकरफाईल कंप्यूटर को बताता है कि बॉक्स में क्या रखना है और अंदर सब कुछ कैसे व्यवस्थित करना है।

# आईये हमलोग इसे एक संख्या का अनुमान लगाएं गेम के उदाहरण से समझते हैं:

1. ## **प्रोग्राम लिखें:** मान लें कि हमलोग अपना पायथन गेम game.py नामक फ़ाइल में लिखा है:

   ## Guess the Number Game

यह एक आसान पायथन स्क्रिप्ट है जो उपयोगकर्ता से 1 से 10 के बीच की संख्या का अनुमान लगाने के लिए कहती है।

```python
import random

number_to_guess = random.randint(1, 10)
print("Guess the number between 1 and 10")

while True:
    guess = int(input("Your guess: "))
    if guess == number_to_guess:
        print("You guessed it right!")
        break
    else:
        print("Try again!")
```

2. ## **एक डॉकरफाईल बनाएँ:** इसके बाद, हमलोग game.py फाइल जिस फ़ोल्डर में है उसी फोल्डर में डॉकरफाईल नामक एक फ़ाइल बनाएंगे। डॉकरफाईल, डॉकर को बताता है कि हमारे कंटेनर इमेज कैसे बनाई जाए।

```dockerfile
# Use a lightweight Python image
FROM python:3.8-slim

# Copy the game code into the container
COPY game.py /app/game.py

# Set the working directory inside the container
WORKDIR /app

# Run the game
CMD ["python", "game.py"]
```

     
3. ## **कंटेनर इमेज बनाएं:** एक बार जब हमारे पास डॉकरफ़ाइल हो, तो हम कंटेनर इमेज बनाने के लिए डॉकर का उपयोग करते हैं। हम लिनक्स सिस्टम पर अपना टर्मिनल खोलेंगे और निचे दिए हुए कमांड चलाएंगे:

   ```bash  
   docker build \-t guess-number-game .
   ```
   इस कमांड से हम डॉकर को डॉकरफाइल में दिए गए निर्देशों का उपयोग करके इमेज बनाने और इमेज को  
   अनुमान-संख्या-गेम नाम देने के लिए कहते  है।

# कंटेनर कैसे चलाते हैं?

जब हमारे गेम का कोड एक इमेज में बदल जाता है, तो उसमें गेम चलाने के लिए सारी ज़रूरी चीज़ें होती हैं। लेकिन इस इमेज का सही से इस्तेमाल करने के लिए, हमलोग  इससे एक कंटेनर बनाएंगे, हम इमेज को एक नक्शे की तरह और कंटेनर को गेम का चालू हिस्सा समझ सकते हैं। जब हम कंटेनर चलाते हैं, तो हम उस इमेज को एक असली गेम में बदल रहे होते हैं। इसलिए, गेम खेलने के लिए, पहले कंटेनर शुरू करेंगे, जो फिर हमारा गेम चलाएगा।

जब इमेज तैयार हो जाती है, तो इसे एक कंटेनर शुरू करने के लिए इस्तेमाल किया जा सकता है। कंटेनर उस इमेज का सक्रिय रूप है, जिसमें प्रोग्राम चल सकता है। हम किसी भी कंप्यूटर पर कंटेनर चला सकते हैं, जिसमें डॉकर या उसके जैसा कोई सॉफ्टवेयर हो।

**उदाहरण :**  
एक बार जब हमलोग इमेज बना लेते हैं, तो हम docker run कमांड का उपयोग करके इसे अपने लिनक्स सिस्टम पर चला सकते हैं।

1. ## **कंटेनर चलाएँ:** इमेज बनाने के बाद, कंटेनर रन करें:

   ```bash  
   docker run \-it guess-number-game  
   ```
   -it विकल्प डॉकर को कहता है की कंटेनर को इंटरैक्टिव रूप में चलाइए, ताकि हम गेम खेल सकें।

2. ## **गेम खेलें:** कमांड चलाने के बाद, हमलोगो को गेम के लिए एक संदेश अपने स्क्रीन पर दिखाई देगा।

   ```bash  
   Guess the number between 1 and 10  
   Your guess:   
   ```

   फिर हम संख्याओं का अनुमान लगाकर गेम खेल सकते हैं, और गेम हमें बताएगा कि हमने सही अनुमान लगाया है या नहीं!

# आइए जल्दी से समझें कि "संख्या का अनुमान लगाएं" गेम कैसे काम करता है:

1. **प्रोग्राम लिखें:** हम एक पायथन गेम लिखते हैं जहां खिलाड़ी एक संख्या का अनुमान लगाता है।  
     
2. **एक डॉकरफाईल बनाएं:** हम एक फ़ाइल बनाते हैं जो डॉकर को बताती है कि हमारे गेम को एक बॉक्स (कंटेनर इमेज) में कैसे पैक किया जाए।  
     
3. **इमेज बनाएँ:** हम गेम की एक कॉपी बनाते हैं और एक कंटेनर इमेज बनाने के लिए डॉकर का उपयोग करते हैं।  
     
4. **कंटेनर चलाएँ:** हम डॉकर का उपयोग करके गेम को एक कंटेनर के अंदर चलाते हैं, और गेम बिल्कुल वैसे ही काम करता है जैसे किसी भी कंप्यूटर पर होना चाहिए।  
   

# निष्कर्ष:

कंटेनर एप्लिकेशन को आसानी से कहीं भी साझा और चलाने की सुविधा देते हैं, बिना संगतता की चिंता के। वे सभी ज़रूरी चीजों को एक पैकेज में रखते हैं, जिसे इमेज कहते हैं, और इसका उपयोग किसी भी सिस्टम पर कंटेनर बनाने के लिए किया जा सकता है। डॉकर जैसे रनटाइम कंटेनर बनाने, चलाने और प्रबंधित करने को आसान बनाते हैं। कंटेनर इमेज, रजिस्ट्रियों और उन्हें बनाने-चलाने के तरीकों को समझकर, हम अपने प्रोग्राम को आसानी से अलग-अलग सिस्टम पर चला सकते हैं।
