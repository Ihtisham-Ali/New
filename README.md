# Table of Contents

 **Livetree / Filecoin VideoJS Player Decentralised Introduction**                                
 **Development Overview**                                                                         
 **Development Roadmap**                                                                          
 **Assumptions**                                                                                  
 **Data Model**                                                                                   
 **Implementation Guide**                                                                         

# Livetree / Filecoin VideoJS Player Decentralised
     ## Introduction
   
  **Strategic Objectives:**

     Within the context of building the next generation Web 3.0 Video, Livetree and Filecoin are releasing a video
player built on top of the popular open-source project VideoJS and featuring the following strategic
enhancements to realise the future of video on a decentralised web:

  **Item Defined:**

     An item represents film, video, TV series, box set or other media elements. Items may contain other items:
in the case of a box set, the “Box” contains several “Series” which in turn contain “Episodes”.

  **Player Goals**

  #Video player feature                                 ##Strategic Goal Description
 
1. **Item Content metadata:**   Metadata describing the video, TV series or film playing and related media assets (such as pictures, subtitle files, which
                                countries the content is licensed to play within for example certain films are geo-blocked for certain jurisdictions).
                                Strategic goal is to make this data Item Content Meta Data publicly available via Filecoin/IPFS so in combination with
                                Item Content Viewing Statistics and Item Audience Data the content can be monetised (AVoD, TVoD, SVoD, or through
                                direct contributions/e-commerce) while being completely transparent and inline with the values of Web 3.0. Item Content
                                Viewing Statistics and Audience Taxonomy are implementations of the specifications put together by the IAB these
                                standards are used by Facebook and many other internet leviathans. The overarching strategic goal is to leverage
                                Programmatic Advertising to create a completely transparent decentralised Private Marketplaces (PMP or similar
                                constructs), where users can use monetise their data through open-source recommendation engines and decentralised
                                PMP market makers. The process being completely traceable using an enhanced IAB programmatic specifications
                                governed by a Polkadot Substrate and underpinned by data stored on IPFS/Filecoin. This document goes some way to
                                starting to define these specifications in the context of IPFS/Filecoin and how they could be implemented at the Video
                                player layer, however, we expect the wider community to enhance and expand on them (all technical artefacts released as Open Source)..


2. **Item Content 
Viewing Statistics:**           Store and secure history of user video viewing events. This can be used for paying royalties (SVod, TVod), advertising
                                insertion (AVoD) and also in future developing an “app store” of open-source recommendation engines. Strategically we
                                want to decentralise these recommendation engines so users and their data are not tied into a “single” recommendation
                                system, for example, right now we see Facebook, YouTube and other internet giants dominating this data and
                                obfuscating the recommendation algorithms to meet their own strategic objectives. Our strategic goal is to provide an
                                IPFS/Filecoin specification so 3rd party open-source recommendation engines can be developed, thereby providing
                                transparency over how our data is being both used and monetised within the context of audience data (PMP) and also
                                within paying direct royalties to content license holders/content creators.



3. **Item Content
Referrals:**                    To assist with attribution as to whom/system/entity referred a user to the particular video viewer. Strategically this enables
                                referral and incentive systems.


4. **Item Transcoding
&amp; CDN support:**            Handle MP4 multi-bitrate files. For example, stream 640 instead of 1040HD based on internet connection speed using
                                decentralised CDN. Strategically enable a scalable global playback.


5. **Item Content
Protection DRM:**               Support both DRM “Hollywood” encrypted and non-encrypted video. Handle both encrypted DRM (Microsoft PlayReady,
                                Widevine and FairPlay Streaming) JSON Web Token (JWT) or Simple Web Token (SWT) to add or validate claims for
                                your and non-encrypted video. Strategic goal is to protect copying of videos by encrypting on the device thus enabling
                                Hollywood content to be licensed to the platform. Support for non-encrypted strategically give us maximum reach.


6. **Item Subtitles &amp;
enhanced A.I.
taxonomy
Support:**                      Speech-to-text video A.I. processing produces subtitle files in a number of formats. Strategically we want the videos to be
                                translated for maximum reach across the globe. A separate taxonomy and spec will be published which will enhance the
                                Item taxonomy associated with each piece of content.



 #Development Overview

The video player is an embeddable widget with two key interfaces elements:

a) **Carousel:**       A scrollable/swipeable panel showing an image with text/title for each element in a given item array.
                       From there the user can drill down into the item (where there are sub-items) or launch the video player for that
                       item;


b) **Player:**         A pop-up panel based on videojs which plays the content (DRM and non-DRM enabled) with VAST
                       extensions to allow pre-, mid- and post-roll ads.


The widget is available/embeddable in three ways:



a) As an npm installable component (both ES6 and CommonJS interfaces supported);

b) In-line referencing code hosted by livetree;

c) As an iframe into a webpage hosted by livetree.

… the source code is open source, from this repo and we encourage the community to extend the following.

The widget takes as input either a json file; or a pointer to the location of a json file stored on-line.


The widget interacts with four key end points:



a) **ItemMetaData:**        [read] source for item data;


b) **Media:**               [read] source for media;


c) **ViewEventLog:**        [write] record viewing events, including the calling domain for referral;


d) **DRMToken:**            [read] source for DRM credential to view protected content.





Development in latest-version Angular [currently 11, but likely to be released under 12].







3. #Development Roadmap

   ##Stage                       ##Goal                                                            ##Metric


     1                  Build initial carousel and player widget; viewing of DRM and              Successful test of embedding widget in all three modes.

                        non-DRM content; viewing stats saved to local storage.


     2                 Implement simple IPFS value-pair storage for viewing events                Successful test of storing events for 3 different user-sessions and recovering data across all sessions.



     3                 Extend storage for viewing events to structured data (eg. OrbitDB)        Successful test of storing events for 3 different user-sessions and recovering data across all sessions.



     4                 Extend storage to Filecoin on-chain.                                      Successful test of storing events for 3 different user-sessions and recovering data across all sessions.



     5                Implement VAST extension to allow in-line ads.                             Successful test of pre-, mid- and post- roll ads


     6               User-interface enhancements to allow selection of subtitles/language        Successful test of 2 different subtitle languages. 
                     and pop-up display of meta-data.







4. # Assumptions


##Description                                                                                 ##Comments

 No user wallet user ids check out ceramic log-in. User details are not assumed.
 Viewing stats logged aliased to a generated number
 which can be swapped for the ceramic wallet id anonymously, 
 unless user detail provided as part of the json used to instantiate the widget.





 Useable DRM token can be supplied via http/https end-point call.



 Referral details will be taken as the domain within which the
 widget is embedded. Additional referrer details can be provided in                             
 the json used to instantiate the widget. 


 Display mode (single or multiple) is derived based on the number                          Possible this can be overridden to single in the json file supplied at instantiation.
 of items provided by the ItemMetaData end-point.





# Data Model


*Logical View of Item Content metadata*





# Web3 Video Player

This project introduces a new *protocol* for distributed video on web3. It aims to provide a integrated video eco-system which supports:
a) Playing of DRM and non-DRM content (using a modified video-js player);
b) Sourcing media meta-data from distributed platforms (IPFS, Filecoin, Polkadot ...) as well as from proprietary sources, stored with the open-source Livetree protocol;
c) Saving viewing events to distributed platforms (IPFS, Filecoin, Polkadot ...) as well as to other proprietary stores;
d) Extensions for use with referral programmes, loyalty programmes, paywalls, royalty distribution.

The project has been developed for livetree (www.livetree.com) with sponsorship from filecoin (www.filecoin.io) and Microsoft (www.microsoft.com).

Further information can be founds here:


## Content Provision

The video-player content can be consumed in a number different ways. 

a) **Hosted DRM Content** To access DRM content, a host is required who can support two endpoints for the web3_video protocol:
	1) *GetItemDetails*. Returning a json object specifying the media item details and associated meta-data (full spec below);
	2) *GetDRMTokens*. Returning the DRM tokens required to access the data (currently PlayReady, Widevine and FairPlay tokens are supported).

	Content can be hosted by livetree, if required. Please contact admin@livetree.com for more details; or if you wish to learn how to host DRM content for distribution via the web3_video protocol.

b) **Self-Hosted DRM Content** If you wish to host your own content, you will generally need to build your own end-points, as above

c) **Non-DRM Content** Non-DRM content (either static or streamed) can be accessed by simple URL reference. livetree may be able to assist with cost-effective media storage if required. Please contact admin@livetree.com	

Note: It is intended that these server-side endpoints will utilise distributed storage technologies, however local storage is anticipated in the short term while those technologies mature.

## Usage

The video-player can be used in a number of ways:

a) URL reference (inc. query parameters);

b) iframe; [iframe functionality requires re-factoring the code to avoid passing the video object through the DOM/window. See TODO list below.]

c) code download.

For both URL reference and iframe, you can pass several parameters as a json options object (*?options={...}*):

a) *itemurl* URL specifying the GetItemDetails endpoint providing media item details and meta-data
b) *drmurl* URL specifying the GetDRMTokens endpoint providing the DRM tokens for the item
c) *linkurl* URL specifying a link to prompt content-viewers to follow if necessary
d) *mediaId* The id of the item to retrieve from the endpoint
e) *referId* A referral id to be used within a referral link
f) *embed* Boolean flag to display embed code (<iframe>)
g) *height* Height of player on screen
h) *width* Width of player on screen

All of the options normally available with videojs should also be valid.

Note: It is intended that a default itemurl, drmurl and linkurl and so on are set by whomever is hosting the web3 video player. These can be overridden within the options, if necessary. These would normally contain [mediaId] and [referId] parameters which would be set using the mediaId and referId values passed.

For test purposes, and as a working example, you can find a hosted version of the player at:

	https://fairweb.livetree.com/web3-video-player/index.html
	
The content and endpoints consumed by this player are hosted by: https://www.livetree.com

Examples:

------ Simple Cases------

https://fairweb.livetree.com/web3-video-player/index.html?mediaId=7736&referId=cbce65637&embed 
https://fairweb.livetree.com/web3-video-player/index.html?options={"mediaId": 7736, "referId": "cbce65637"}
https://fairweb.livetree.com/web3-video-player/index.html?src=http://commondatastorage.googleapis.com/gtv-videos-bucket/sample/BigBuckBunny.mp4
https://fairweb.livetree.com/web3-video-player/index.html?options={"src": "http://commondatastorage.googleapis.com/gtv-videos-bucket/sample/BigBuckBunny.mp4"}

------ Extended Cases------

https://fairweb.livetree.com/web3-video-player/index.html?options={"mediaId": 7736, "referId": "cbce65637", "linkurl": "www.mywebsite.com/referrals?myagent=[referId]}



https://fairweb.livetree.com/web3-video-player/index.html?options={"src": "http://commondatastorage.googleapis.com/gtv-videos-bucket/sample/BigBuckBunny.mp4", "type":

"video/mp4", "referId": "12345ABC", "linkurl": "https:www.mysite.co.uk/ambassadors?ambassador=[referId]"}

https://fairweb.livetree.com/web3-video-player/index.html?options={"src":

"http://commondatastorage.googleapis.com/gtv-videos-bucket/sample/BigBuckBunny.mp4", "type":"video/mp4", "linkurl":

"https:www.mysite.co.uk/ambassadors?ambassador=12345ABC"}

https://fairweb.livetree.com/web3-video-player/index.html?options={"itemUrl":

"https://fairweb.livetree.com/api/Web3Extensions/GetItemDetailsById?mediaId=7736&branchReferrerUserName=cbce65637", "drmUrl":

"https://fairweb.livetree.com/api/Web3Extensions/GetDRMToken?", "linkUrl":

"https://www.mywebsite.com/landingpage"}

https://fairweb.livetree.com/web3-video-player/index.html?options={"itemUrl":

"https://fairweb.livetree.com/api/Web3Extensions/GetItemDetailsById?mediaId=[mediaId]&branchReferrerUserName=[referId]", "drmUrl":

"https://fairweb.livetree.com/api/Web3Extensions/GetDRMToken?", "linkUrl":

"https://www.mywebsite.com/landingpage", "mediaId": 7736, "referId": "cbce65637"}



NOTE: The json parser expects field names to be encapsualted in *quotes*. The most common error is badly formatted json options.

Any correctly formatted urls can be consumed in simple wepages via an <iframe>. Examples:

<iframe src='https://www.livetree.com/web3/video-player?options={"mediaId": 7736, "referId": "cbce65637"}'></iframe>


The iframe code can be extracted at any point directly from the player itself by clicking on the bottom right section of the player window, and copying the text exposed.

## Build environment
This project was initially generated using Angular but has been converted to basic stand-alone javascript without a CLI framework (such as Angular or React) and without reference to any external modules (such as npm).

## Build Overview

The build works via 4 key scripts:
a) *web3-video-config.js* Config parameters to provide endpoints for media item protocol data and drm tokens. These can be amended for custom use as required.
b) *web3-video-events.js* Player events (create, start, stop and so on) are recorded to IPFS for later push to filecoin (or other web3 storage as required by your usage). 
c) *web3-video.js* Main 'workhorse' of the player. This is adpated from core videojs and a number of plugins (contrib-eme, overlay-hyperlink, contrib-quality-levels, http-source-selector, titleoverlay, embed). A special injector script creates a custom *initPlayer(id, options)* function which pulls these plugins together and initiates the enhanced video player.
d) *web3-video-source.jss* This accesses the media and drm token protocol endpoints. Custom sources can be introduced into the *getWeb3VideoProtocol* function as indicated, if useWeb3ApiEndpoints is set to false in config.

These scripts are injected into <head> in index.html, along with the necessary .css.

<head>
...
  <link href="scripts/web3-video.css" rel="stylesheet">

  <script src="scripts/web3-video-config.js"></script>
  <script src="scripts/web3-video-events.js"></script>
  <script src="scripts/web3-video.js"></script>
  <script src="scripts/web3-video-source.js"></script>
...
</head>

The web3 video element should be set in the body, with id "web3-video", and a small script is added after this which calls the initPlayer function to initialise.

<body>
  <div class="content" role="main">
    <video 
      id="web3-video"
      class="video-js vjs-big-play-centered"
      controls
      preload="auto"
      width="800"
      height="600">
    </video>
  </div>
  <script src="scripts/web3-video-init.js"></script>
</body>



The main config parameters can be set up-front:

//-------------------------------------------------------------------------------------
// Set useWeb3ApiEndpoints to *false* if supplying Media data via an alternate function - to be specified in getWeb3VideoProtocol function in web3-video-sources
//private web3BaseApiUrl = "https://fairweb.livetree.com/api/Web3Extensions/";
web3BaseApiUrl = "https://fairweb.livetree.com/api/Web3Extensions/";
config_optionsDefaults = { ///add below items into this object
  useWeb3ApiEndpoints : true,
  web3VideoItemProtocolEndpoint : web3BaseApiUrl + "GetItemDetailsById?itemId=[mediaId]&branchReferrerUserName=[referId]",
  web3VideoDRMTokenEndpoint : web3BaseApiUrl + "GetDRMToken?mediaElementId=[elementId]&itemId=[mediaId]",
  web3VideoDRMCertificateUri : "https://www.livetree.com/fairplay.msbs",
  web3VideoItemProtocolStatsEndpoint : web3BaseApiUrl + "SaveStats",
  web3VideoDRMQueryString : "?mediaElementId=[elementId]&mediaId=[mediaId]",
  web3VideoEmbedQueryStringItem : "?mediaId=[mediaId]&referId=[referId]",
  web3VideoEmbedQueryStringSrc : "?src=[src]&type=[type]",
  videojsCTAOverlayButtonLink:  "https://www.livetree.com?branchReferrerUserName=[referId]",
  IPFSNode:  "https://ipfs.infura.io:5001/api/v0/add" }
//-------------------------------------------------------------------------------------
  
  
On initialisingm, the video player:
	a) Gets default options from config;
	b) Gets any option supplied in-line in html;
	c) Parses the URL for options supplied in Query Parameters;
	d) Gets the media item protocol using the parameters passed (if an itemUrl is specified)
	e) Gets the media DRM protocol using the parameters passed (if a drmUrl is specified)
	f) Initialise the video using these options.

The code can used as an example and modified to your requirements as necessary. Most of the parameters specified can be over-ridden by either in-line html or from Query Parameters passed in via URL.

Bespoke event save routines can be used to replace (or alongside) the *pushIPFS(data)* function.


## Media Item Endpoint Protocol

    // This expects to return data in the following structure, retreived from the endpoint provided in itemUrl
    // Strucure is extended to support future enhancements
    //
    //    mediaId = Id,
    //    MediaElementId = // will give you a shortcut to the MediaElementId with the video of type 999
    //    CoverPic = MediaDefaultLiveTree.FileUrl,
    //    TrailerUrl = Trailer?.FileUrl,

    //     MediaElements = arrray[] of MediaElements 
          //{
          //    MediaElementId: int,  
          //    MediaType: int,
                //Advertising = 100,
                //TrailerMediaType = 600,
                //AmsVideo = 999,
                //Video = 888,
                //Poster = 111,
                //SecondPosters = 112,
                //Vtt = 555
          //    MIMEType: string,
          //    IsAudio: boolean,
          //    IsVideo: boolean,
          //    CdnHlsV3Url: string,
          //    CdnSmoothStreamingUrl: string,
          //    CdnPegDashV4Url: string,
          //    CdnHlsV4Url: string,
          //    LicenseSmoothStreamingWidevineUrl: string,
          //    LicenseSmoothStreamingPlayreadyUrl: string,
          //    LicensePegDashV4WidevineUrl: string,
          //    LicensePegDashV4PlayreadyUrl: string,
          //    LicenseHlsV3FairPlayBaseLicenseAcquisitionUrl: string,
          //    LicenseHlsV4FairPlayBaseLicenseAcquisitionUrl: string,
          //    CdnCommonEncryptionKid: string,
          //    CdnCommonEncryptionCbcsKid: string,
          //    GeoCheckApprovedCountriesCommaSeparatedIsoCodes: string,
          //    GeoCheckRejectedCountriesCommaSeparatedIsoCodes: string,
          //    IsPublic: boolean,
          //    FileExtension: string
          //};

    //    Price: number,
    //    ItemForm : string,

    //    SeedTotalRaisedToDate: number,
    //    SeedTargetTotalRaiseAmount: number,

    //    PublishRewardType: string,
    //    PublishRewardAmount:  number,
    //    PublishRewardPercentage: number,
    //    PublishTypeDesc: string,
    //    PublishType: string,
    //    PublishTypeDonationAmount: number,
    //    PublishTypeDonationQuantity: number,
    //    PublishTypeDonationReserveAmount: number,
    //    PublishTypeFixedPriceBuyPrice: number,
    //    PublishTypeFixedPriceQuantity: number,
    //    PublishTypeFreeQuantity: number,
    //    PublishTypeSubscriptionBuyPrice: number,
    //    PublishTypeSubscriptionPeriodType: string,
    //    PublishTypeSubscriptionPeriodTypeOtherFrequency: string,

    //    Title : string,
    //    SubTitle : string,
    //    IMDBId : string,
    //    Actors : string, [can be comma separated]
    //    Genres : string, [can be comma separated]
    //    Description : string,
    //    KeyWords : string, [can be comma separated]
    //    Category : string
    //

## DRM Token Endpoint Protocol

    // This expects to return data in the following structure, retreived from the endpoint provided in itemUrl
    //
    // ClientIpAddress: string
    // TokenWidevine: string
    // TokenPlayReady: string
    // ErrorMessage: string (expecty null )
    // ErrorCode: int
    // UserDevice: string

## Planned Enhancements (TODO)

1.	Update the mechanisms to inject the videojs player for consumption in the Angular app, to avoid passing it via the window/DOM (as this prevents iframing the app). This may require the full re-factoring outline in item 4 below [Done: 04.04.2021]
2.	Enhance IPFS save json structure: specifically to chain (DAG) saved packets together for sequential retrieval. Will need a queue mechanism to wait for returned cid to supply to next packet.
3.	Enhance IPFS save function to push to filecoin.
4.	Convert angular module to run entirely as in-line code which can be injected into the <head> with other plugin scripts - removes dependency on Angular, and ideally also npm, or other 'bloatware' development environments. [Done: 04.04.2021]
5.	Enhance the embed iframe code generator to automatically push the code to the copy-paste buffer instead of requiring the user to manually copy.
6.	Update the .css so that the button text can be made visable. [Done: 02.04.2021]
7.	Add ability to play subtitles for DRM content (selectable from a list of vtt tracks provided). [Done: 02.04.2021]
8.	Add skip forward and backwards controls to allow jump 30s.
9.	Fade *More ...* button back in at end of reel.
10.	Add config file to DOM instead of in code header of Angular module. [Done: 03.04.2021]
11.	Review end-point interfaces specs (simplify on a single mediaId and remove the need for mediaElementId). Return DRM url and media-specific link url along with other media meta-data. Clean-up termiinology areound mediaId and mediaId.
12.	Add playlist functionality (or a form of carousel) so as to be able to retrieve and manage a 'stack' of media rather than a single item. An additional endpoint may be needed to supply a media stack. (We refer to these stacks as *communities* since the intention is that each media stack would have a common theme for an interest group, and meta data regarding the interest group would be maintained in addition to the media data.)
13.	Update json parsers to me more resilient to 'case' and field names without quotes.[Done: 02.04.2021]
14.	Review initialization process to see if InitPlayr can be triggered automatically without the need for a script in the <body> after the video element.

------------Standard ReadME below ----------------

## Development server

Build uses light-server for serving page during development. [https://www.npmjs.com/package/light-server]

 - npm install light-server
 - light-server -s .
 
Note: look at light-server help for guidance on watching files for changes and auto-reaload.

avigate to `http://http://0.0.0.0:4000/`. The app will automatically reload if you change any of the source files specified for light-server


## Code scaffolding

None.

## Build

No build is required. Code is already native js.

## Further help

For further help please contact admin@livetree.com.
