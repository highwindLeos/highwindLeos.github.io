---
layout: single
title:  "Jekyll Gallery"
categories : Jekyll
tag : [Jekyll, Blog, Markdown]
toc : true 
author_profile : true 
sidebar : 
    nav : "docs" 
search : true 
gallery:
  - url: ../images/Profile_1.gif
    image_path: ../images/Profile_1.gif
    alt: "Profile Emoticon"
    title: "Profile Emoticon"
  - url: ../images/Profile_3.jpg
    image_path: ../images/Profile_3.jpg
    alt: "Profile Emoticon"
    title: "Profile Emoticon"
  - url: ../images/Profile_2.gif
    image_path: ../images/Profile_2.gif
    alt: "Profile Emoticon"
    title: "Profile Emoticon"
gallery2:
  - url: https://flic.kr/p/8a6Ven
    image_path: https://farm2.staticflickr.com/1272/4697500467_8294dac099_q.jpg
    alt: "Black and grays with a hint of green"
  - url: https://flic.kr/p/8a738X
    image_path: https://farm5.staticflickr.com/4029/4697523701_249e93ba23_q.jpg
    alt: "Made for open text placement"
  - url: https://flic.kr/p/8a6VXP
    image_path: https://farm5.staticflickr.com/4046/4697502929_72c612c636_q.jpg
    alt: "Fog in the trees"
---

**[Notice]** [겔러리 삽입법.](https://mmistakes.github.io/minimal-mistakes/docs/quick-start-guide/){: target="_blank" }
{: .notice--danger }

# 겔러리 삽입법 정리

둘 이상의 이미지가 있는 배열의 선택적 캡션을 사용하여 <그림> 요소를 생성합니다.
갤러리를 배치하려면 필요한 YAML Front Matter를 추가합니다.

```yml
gallery:
  - url: /assets/images/unsplash-gallery-image-1.jpg
    image_path: /assets/images/unsplash-gallery-image-1-th.jpg
    alt: "placeholder image 1"
    title: "Image 1 title caption"
  - url: /assets/images/unsplash-gallery-image-2.jpg
    image_path: /assets/images/unsplash-gallery-image-2-th.jpg
    alt: "placeholder image 2"
    title: "Image 2 title caption"
  - url: /assets/images/unsplash-gallery-image-3.jpg
    image_path: /assets/images/unsplash-gallery-image-3-th.jpg
    alt: "placeholder image 3"
    title: "Image 3 title caption"
```

그리고 갤러리에 드롭인(drop-in)을 하면 원하는 본문이 나타납니다.

|Name|필수|설명|
|----|:---:|---|
|url|옵션|URL to link gallery image to (eg. a larger detail image).|
|image_path|필수|Full path to image eg: /assets/images/filename.jpg. Use absolute URLS for those hosted externally.|
|alt|옵션|Alternate text for image.|
|title|옵션|Title text for image. Will display as a caption in a Magnific Popup overlay when linked to a larger image with url.|


{% include gallery caption="Profile EmotiCon" %} 

갤러리 뒤에 있는 텍스트입니다. 모든 것이 올바르게 정렬되어 있는지 확인합니다.
이번에는 세팅 id YAML 프론트 매터의 두 번째 갤러리 해시에 일치시킵니다.

{% include gallery id="gallery2" caption="Out sourcing" %}

**[TIP]** *layout="half"* 를 include 에 속성으로 추가하면 절반 레이아웃으로 변경됨
{: .notice--primary}

[Mmistakes Link](https://mmistakes.github.io/minimal-mistakes/docs/helpers/#gallery){: .btn .btn--danger target="_blank"}