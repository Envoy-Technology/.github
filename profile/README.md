## 🌟 1 - What is Envoy ? 

#### 1.1. The Envoy flow
We help you (content apps) use your content to attract qualified leads. We do this by placing content previews inside a high-converting web flow we host on your behalf. 

<figure class="">
    <img src="https://github.com/Envoy-Technology/.github/blob/main/images/player_views_1.png?raw=true" style=""/>
</figure>

#### 1.2. Features
There are two key ways for you to use the Envoy flow, through **gifting** and **marketing** links:

| Feature     | Short description |      Integration needed?        | Illustrated example |
| ----------- | ----------------- | ------------------------------- | ------------------  |
| Gifting      |   Enable your users to share with their friends.   |   Yes, an API call to get gift link + a gift button on the front-end    | <img src="../images/player_views.png" style="width: 300px;"/>       |
| Marketing links   | Generate links to be shared on social media or email campaigns   |    No, gets done from dash in a no-code way    | <img src="../images/player_views.png" style="width: 300px;"/>       |
| Rewards   | Boost sharing by creating incentives for your users   |    It depends on implementation (ie rewarding signups means integrating our pixel)   | <img src="../images/player_views.png" style="width: 300px;"/>       |
| Analytics   | Generate links in a no-code way                     |    No | <img src="../images/player_views.png" style="width: 300px;"/>       |

#### 1.3. Supported formats 
| Format     | Image |      
| ----------- | ----------------- |
| Video      |   Enable your users to share with their friends.   
|  Audio | Generate links to be shared on social media or email campaigns |
| Live audio and video |   Enable your users to share with their friends. |  
| Articles   | Boost sharing by creating incentives for your users   |   

## 🛠️ 2 - How do I integrate Gifting into my app?
After you've set up your space in the Envoy dash, here's the API call you'll need to make to get a link (example in Python). 
``` 
import requests

api_key = "-----"
API_endpoint = "https://api.envoy.is/partner/create-link"
source = "----.mp3"
customer_journey_conf = {
    'userId': '100',
    'contentConfig': {
        'contentType': 'VIDEO',
        'contentId': 'your-content-id',
        'contentName': 'Your content name',
        'contentDescription': 'Your content name description',
        "common": {
            "media": {
                "poster": "https://your-poster-uri.com",
                "source": source
            }
        },
    }
}

response = requests.post(
    API_endpoint,
    headers={
        "x-api-key": api_key,
        "Accept": "application/json",
        "Content-Type": "application/json",
    },
    json=customer_journey_conf,
)
```

The respond payload will contain a `url` and a `userRemainingQuota`. Link format is:  `[your_app_name].envoy.gift/12345`.

## 🔒 3 - How do you access my content in a secure way?

#### 1 - How we display content  
We stream directly from your CDN's servers and never host anything ourselves. We serve the content in our own player inside an webpage hosted by us, built on Shaka Player. Shaka Player has great performance, can handle large video streams (it's used by many streaming platforms).

#### 2 - How we access your content in a secure way  
-   We are pretty flexible when it comes to accessing Your content in safe way: we support several strategies: access token-based auth, header-based auth.
-   We also have a system of signed urls that, for your CDN can check and be 100% certain requests comes from Envoy.

#### 3 - How we keep it secure while streaming it  
We're compatible with the DRM protection you have in place, you can give us 1 DRM certificate by DRM system (FairPlay, PlayReady, Widevine) for each video.





 
