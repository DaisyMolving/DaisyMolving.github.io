---
layout: post
comments: true
title:  "Design Pairing Tour: Day 3"
date:   2019-05-22 00:00:00 +0000
---

My third day of Design pairing was with my mentor, Eva PenzeyMoog, and we worked at a client office. The client is a large Design agency that has hired 8th Light to implement a mobile application for both iOS and Android. Apart from creating functionality, the implementation also requires application of good accessibility practices. Today we were focussing on accessibility for blind and visually impaired users on Android devices.

After Eva had explained the background of the project, I set up TalkBack, a tool for the visually impaired, from the Android Accessibility Suite on my android phone. TalkBack interacts with android and its apps as a screen reader and also changes movements to suit partially and non sighted people's usage needs. I used the TalkBack tutorial, without looking at my screen, in order to learn controls and movements from listening alone. It was at times quite difficult for me, and was a good exercise in building empathy.

Afterwards I looked at how some applications interact with TalkBack to determine their level of accessibility. I looked at some apps that I already had on my phone, and some others that I downloaded that were specifically for blind and visually impaired people, to see how they might compare. They were Uber, Facebook Messenger, Asana Rebel and ChessBack Beta.

Uber:

- On opening, TalkBack announces "Uber, google map". While this is helpful in terms of knowing that there is a map present, the lack of *specific* labelling about what the map is, or shows, is not helpful. I thought that some announcement like "Map showing your current location and nearby uber cars", or something else more descriptive, could be a good alternative. Also the call to action on that first pace, which is an input with placeholder "Where to?", is not announced at all. The user would have to move over the page to find it. This doesn't make the Uber app as helpful for finding a car to ride in for those who cannot see the action easily.
- In menu, when focussed on profile picture, TalkBack announces "unlabelled button". This could be frustrating and also potentially unsettling - would you activate a button if you didn't know what it does? This is something to keep in mind when a button does not contain text (that would be read), but when it's meaning is portrayed by a different visual element.
- On 'Your Trips' page, seems things can be ordered. For instance, although the back button appears before the page title, the page title is announced first. This is useful as the user can know where they have landed before they decide to seek/select the back button.
- Overall Uber's accessibility in terms of its interaction with TalkBack was not very good, which surprised me as I thouht that it is a service that could be used often by a blind or visually impaired person.

FB Messenger:

- Messenger functionality is full of text elements, so navigation works well with TalkBack.
- One frustration was having to move through all "Friend Stories" horizontally (when swiping down), before reaching the messages. I would expect the messages to be the primary actions on the page, and stories to be secondary.

Asana Rebel:

- I looked at Asana Rebel as it is an exercise, yoga, lifestyle app and so I thought it *might* have some similarities with Abound being a health, lifestyle type app.
- Asana Rebel contains a *lot* of visual elements and videos, which read as "unlabelled buttons"... argh!
- Some of those elements, that look like videos with play buttons on top, are in fact images instead, and these images do not have content descriptions.
- The "Favourite" or "Like" heart button is not labelled, so it is announced as "not ticked tickbox". Would you activate a tickbox if you didn't know what it did? These "not ticked tickbox"es are on every single workout video (the main content of the app), and all of them are focusable, so that is a lot of noise where the user is unsure what this is.
- When going through a list of workouts (swiping down), only the "not ticked tickbox" favourite buttons are focusable, not any text that would explain that each workout is. This makes the app incredibly unusable.
- Overall, Asana Rebel's accessibility when using TalkBack was *terrible*.

ChessBack Beta:

- ChessBack Beta is an app for playing chess that is made specifically for blind and visually impaired people, so it not only used TalkBack well, but also had some other features that made it very accessible.
- The opening page consists of just the title and menu. TalkBack announces the title as being "out of list". This is helpful to know that this text element is not an option within the menu, so user will not seek to activate it.
- The list of menu options is immediate and simple. By this I mean it is organised well and on the page there are no unneccessary or extra items such as visual elements. Visual elements come later, for gameplay.
- Every square on the chess board is labelled with its co-ordinates, and as the player moves over the board with their finger, TalkBack announces the co-ordinates so they know their position.
- Pieces are labelled simply and consistently as 1. colour, 2. type, 3. position. For example, "black rook E4". This is very clear.

Other non-TalkBack features that made made ChessBack Beta very accessible to blind and visually impaired people were:

- "Wake-lock" prevents phone sleeping while player decides move.
- The option to change colours and patterns on the chessboard squares, which could help a partially sighted person see contrasts to help their gameplay.
- The option to set up sounds to play when opponent moves.
- The option to can increase highlighting (a bright colour on squares) that shows recent moves.

Moving through each of the apps using TalkBack pointed out many features and ways of doing things that helped me to understand how to make our client's more accessible. We had 5 onboarding screens to work on, and we ensured that we added relevant content descriptions where images were conveying meaning, as well as ensuring that calls to action were focussable in a coherent order. The app was written in Kotlin and used XML data to populate the views. This was also quite unfamiliar to me, so it was fun figuring out with Eva how to get this working!

Tomorrow I am going to be working alongside Kevin Kotowski, who works to lead and co-ordinate many of the Design Team's projects. I will be getting a view of project management, leadership meetings and how Design exists as a product. I am looking forward to it, as I don't yet know much about how this side of the business works.
