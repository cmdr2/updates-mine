---
slug: what-would-programming-on-mobile-look-like-part-1
date: 2021-08-15 19:36:35
tags: ['programming-on-mobile']
title: What would programming on a mobile look like? (Part 1)
---

__tl;dr:__ I haven't proposed a concrete solution yet, I'm starting this up as a hobby project, to explore more productive ways to program on mobile devices. This post is the background, question and initial ideas for the solution. Part 2 intends to describe one concrete experiment - trying to build a new text-based syntax that's productive to type on mobile keyboards. It's possible that's the wrong approach, maybe the answer is visual (e.g. nodes-based visual programming), but I'm starting with text for now (principle of least surprise).

## Background (you can skip this) ##

Mobile devices (smartphones/tablets) are good for creating photos, video, audio, but currently aren't good for creating and expressing logic (i.e. programming). It's possible to write and run programs on mobiles (SL4A, Python on Android, along with dev-focused keyboards etc), but it always feels like the productivity is very far from its potential.

Developer-focused touch keyboards feel pretty unproductive due the constrained typing space after fitting all the special characters, and regular touch keyboards require paging through screens of different characters for common operations like inserting square brackets for an array.

A portable wireless keyboard is a valid option. But it's an additional thing to always carry around, especially since I find a touchscreen keyboard good enough to express my thoughts on (for regular email/messaging/typing, even long messages). Swype or voice-typing have become quite good. Physical keyboards are certainly way better, but touchscreen keyboards are good enough. Annoying, but good enough. This opinion is subjective to my usage, language etc.

IMO the issue is that the syntax of most programming languages are designed around physical keyboards, not touchscreen keyboards. The syntax assumes quick and easy access to special characters, and effortless use of Shift+something for doubling the amount of keys and characters available. These two assumptions are not true on a touchscreen keyboard.

Of course it's fair to argue that a phone isn't meant to be used for programming. I respectfully disagree. :) It's also fair to ask how often would I really program on the phone/tablet? If I'm at home/office, I have a laptop which is conveniently available to program on. And when I'm outside, do I really program that much? I've certainly programmed on long train/bus rides, or in boring outdoor situations, but is that really frequent enough? Probably not, but this feels like a fun project, so I'm just going to ignore all that :)

And if you're philosophically-inclined, it's interesting that an entire generation of people (and future generations) are growing up with mobile devices as the only computers in their house. Should they not play with programming while growing up?

## The Question ##

Regardless of the validity of the justifications, I've been wondering - "what would a programming syntax look like, if designed to be productive to type on mobile touch-screen keyboards"?

## The Answer ##

There is obviously no one-size-fits-all answer. And I don't expect a great answer to emerge straight-away, but rather from poking at the problem-space with different experiments.

It's possible the answer isn't literally a new "text syntax", but rather visual, by connecting logic nodes (like in Unreal Engine or Blender). But I'll start with text, in the spirit of least surprise.

In this (hopefully first of many) post, I'm just covering initial thoughts about the syntax design and constraints.

## Who is the user? ##

The answer-spectrum is wide. If the goal is expressing logic productively, then visual programming, on-device app-builders, Excel, in-game configuration, Kerbal Space Program, and traditional programming languages like Python etc - these are all valid solutions. And the answer will be different depending on the target audience - kids in mobile-only households, experienced programmers getting bored outdoors, etc.

So I'd rather start with myself as the target audience, even if I don't represent a large demographic. Experienced programmer getting bored outdoors. The "outdoors" part is probably not that important. It might be, but for now I'll assume no. The situation would be whenever I find myself with significantly easier access to a mobile device, as compared to a laptop.

## Do we need a new programming language? ##

No, I don't think so. IMO the problem is with the syntax, not the programming language itself. So I could start by designing a different syntax for Python, which I find quite balanced as a language. A syntax that's faster to express on mobile, but runs Python underneath.

## Ideas for the first experiment ##

### Syntax: ###

Unsurprisingly, I find text faster and more powerful than visual programming, and I have no problems with typing whole english sentences on a mobile. So text-based.

Obviously special characters (other than period [.] and comma [,]) are a strict no-no. Typing whole english words using swype or auto-suggest or voice dictation is pretty productive for me. So maybe the syntax is whole english words.

And when I say whole english words, I don't mean fancy chatbot AI/NLP or loose grammar that understands anything you say - there'll be strict grammar, similar to how most programming languages work today. No need to reinvent everything at once.

The same fundamental constructs make sense: variables, arithmetic, conditionals, loops, functions, classes, packages. Maybe starting with a productive subset makes sense, initially.

### Tooling: ###

While not strictly part of the syntax, the idea is to make programming productive on mobiles.

So a basic REPL or a basic IDE makes sense. Nothing fancy, just being able to type programs, run them, view the output, switch tabs and manage a rudimentary concept of "project". This would include the interpreter.

Python's "batteries-included" approach makes sense. Being on a mobile, access to the device sensors and interacting with the device capabilities would be good. I should be able to hack up quick programs where I can use my location, accelerometer data, make some web calls etc. In-built libraries for those make sense.

Being able to run programs in the background makes sense, even though phone OSes (for good reason) make it really hard to run things reliably in the background. If I start a numpy task, and get a phone call that lasts for half an hour, my gradient descent should keep running in the background until it finishes. I'm adult enough to understand and manage my phone's battery :) and phone batteries have become really good now.

## Closing thoughts ##

Posts containing vague and high-level design ideas (like this one) usually end up going nowhere. I hope for this to be an exception. This project has been an itch of mine for several years - I bought my first Android phone ten years ago for the precise reason of wanting to program on it (vs a closed iPhone), and to use Google Maps (I had moved to a new city).

In my next post, I'm planning to write a few simple programs with an experimental new syntax, following the design constraints I mentioned above. I'll try to get atleast one solution (however imperfect) for basic concepts like variables, arithmetic, conditionals, loops, functions and classes - using only whole english words, period (.) and comma (,).

Cheers,

cmdr2

dev@cmdr2.org

