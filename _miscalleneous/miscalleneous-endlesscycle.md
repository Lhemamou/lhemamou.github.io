---
title: "EndlessCycle: Building an AI-Powered Bridge Between Lives"
collection: miscalleneous
permalink: /miscalleneous/endlesscycle
date: 2024-12-28
---

The idea of finding your historical doppelganger has always fascinated me. There's something deeply compelling about the notion that somewhere in the vast tapestry of history, someone might have shared our features, our expressions, perhaps even our spirit. This fascination led me to create [EndlessCycle](https://endlesscycle.quest), a web application that uses AI to find your historical twin. Like many passion projects, it started with a simple question: "What if we could build a bridge between faces across time?"
![EndlessCycle Cover](/images/endlesscycle_image.png)

## The James Leininger Story: From Tall Tales to Tech Inspiration

![James Leininger](/images/james_leineger.jpg)


The name EndlessCycle was actually inspired by the fascinating (though likely embellished) story of James Leininger. In the early 2000s, this tale about a young boy supposedly remembering his "past life" as a WWII pilot made quite a splash in the media. While the story has been largely debunked - like many similar claims - it sparked an interesting thought: what if we could actually find historical figures who looked like us?
Not because of reincarnation or mystical connections (sorry, crystal lovers!), but simply because with billions of human faces throughout history, there's bound to be some fascinating lookalikes out there. It's like that party trick where you tell someone they look exactly like a celebrity, except we're playing it with the entire course of human history!


## The Medieval Meets Modern Tech

I decided to lean hard into the mystical aesthetic, not because I believe in past lives, but because it's just plain fun. The interface, built with Svelte, deliberately channels that "mystical fortune teller" vibe with deep purples and blacks, medieval fonts, and ethereal animations. Think of it as a high-tech carnival attraction - entertainment with a dash of historical education thrown in.

## The Mirror's Interface: A Portal Through Time

The UI is designed to be both mystical and intuitive. When you first enter EndlessCycle, you're greeted with a medieval-inspired interface that feels like stepping into an ancient fortune teller's chamber. The main feature is a "mirror" - really just a fancy drop zone where you can either click to upload your image or drag and drop it. While your image is being processed, you'll see a purple spinning wheel (because loading bars are so 21st century) and the message "Traversing the threads of time..."

Once your historical twins are found, you're presented with a beautifully formatted cards showing their portrait alongside various details about their life - birth year, death year, occupation and a link to their wikipedia page. It's like getting a historical baseball card of your doppelganger! 

## Behind the Mirror: Technical Sorcery
The backend is built with FastAPI, which handles all the image processing and communication with our face-matching system. When you upload a photo, several things happen:

1. Your image is processed using [DeepFace](https://github.com/serengil/deepface) with the Facenet512 model, which creates the embedding of your face
2. This embedding is compared against our database of historical figures using Milvus, a vector similarity search engine
3. The closest matches are retrieved along with their historical metadata

## The Historical Archive: Vector Database Magic
At the heart of EndlessCycle lies a Milvus vector database, hosted on Zilliz Cloud. Think of it as a vast library where instead of organizing faces by traditional categories, we organize them by their mathematical similarities. Each historical figure in our database has:

- A 512-dimensional face embedding vector 
- Biographical data (name, birth/death dates, occupation)
- Links to portraits and Wikipedia pages

We chose the cosine distance metric for our face comparisons because it's particularly good (see [this paper](https://scholar.google.com/citations?view_op=view_citation&hl=en&user=hEpTGR0AAAAJ&citation_for_view=hEpTGR0AAAAJ:rO6llkc54NcC)) at measuring the similarity between face embeddings.
The vector similarity search is blazingly fast, taking mere milliseconds to find your historical twin among thousands of faces - much faster than having to flip through dusty portrait galleries!

## Why Svelte as frontend ? A Backend Developer's Gateway to Frontend Mag

Like the mystical mirror at the heart of EndlessCycle, choosing Svelte was about finding a reflection of my backend-focused mindset in the frontend world. As someone more comfortable with Python's straightforward syntax and clear documentation than the sometimes arcane world of frontend frameworks, Svelte felt like finding a familiar face in a historical portrait gallery.
Unlike its more established cousins React and Vue, Svelte speaks a language that feels natural to backend developers. There's no complex incantations of virtual DOM or state management to master - just write HTML, CSS, and JavaScript with a sprinkle of reactive magic. The syntax feels as clean as Python, with transitions and animations that made creating our mystical interface feel less like coding and more like painting.

Ironically, while Svelte made development easier for me, it proved to be a bit of a challenge for our AI coding assistants. These modern-day oracles, trained primarily on React and Vue examples, sometimes struggled with Svelte's unique approach - much like a time traveler trying to use a smartphone in medieval times.

## What's Next: Future Prophecies
While I'm delighted with how EndlessCycle is currently bridging faces across history, I have several enchanting improvements planned:

1. Automatic Historical Updates: History isn't just in the past - it's being made every day. I'm working on an automated system to update the vector database as notable figures pass away and enter the historical record. It's a bit morbid, but hey, at least they'll live on as potential matches in our mystical mirror! I plan to set up automated pipelines to keep our historical database eternally growing.
2. Underground Marketing: Taking inspiration from Alternate Reality Games (ARGs), I'm planning to design some QR codes to place in unexpected locations - coffee shops, bars - each promising to reveal "your past life." I love the idea of turning the real world into a treasure hunt for historical connections. Plus, there's something delightfully fitting about using mysterious symbols to draw people to a face-matching oracle!
3. Enhanced Face Matching: My current matching system sometimes struggles with certain types of images, particularly black and white photos or portraits with unusual lighting or artistic styles. I'm working on improving the preprocessing pipeline to handle these edge cases better. 
4. Speed Improvement: While "traversing the threads of time" sounds mystical, I know waiting too long for results breaks the illusion. I'm optimizing the backend processes to reduce the time between uploading your image and receiving your historical match. This includes caching strategies, better image compression, and possibly switching to a faster face detection model for the initial preprocessing step.

Whether these improvements will lead to more accurate historical twins or just more entertaining matches remains to be seen. But I'm excited about each step forward. Just remember - if you spot a mysterious QR code in your local café promising to reveal your historical doppelganger, you might have found one of my portals to the past!

If you want to give it a try, here's the link: [EndlessCycle](https://endlesscycle.quest)

