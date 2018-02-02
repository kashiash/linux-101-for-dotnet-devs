title: Linux 101
subtitle: ... for .NET Devs
class: animation-fade
layout: true

<!-- This slide will serve as the base layout for all your slides -->

.bottom-bar[
{{title}}
]

---

class: impact

# {{title}}

## {{subtitle}}

.title-oli[
Oliver Sturm &bull; @olivers &bull; oliver@oliversturm.com
]

.title-logo[
<img src="template/devexpress.png" id="devexpress" alt="DevExpress"><img src="template/mvp.png" id="mvp" alt="MVP">
]

---

## Oliver Sturm

* Training Director at DevExpress
* Consultant, trainer, author, software architect and developer for over 25 years
* Microsoft C# MVP

* Contact: oliver@oliversturm.com

---

## Agenda

* One
* Two

---

## On Day 1...

```
From: Linus Benedict Torvalds
Date: August 25 1991
Subject: What would you like to see most in minix?

Hello everybody out there using minix -

I'm doing a (free) operating system (just a hobby, won't be big and
professional like gnu) for 386(486) AT clones. ...

PS. ... It is NOT protable (uses 386 task switching etc), and it
probably never will support anything other than AT-harddisks, as
that's all I have :-(.
```

Full thread: http://osturm.me/torvalds-linux-announcement

--

.overlay[.overlay-content[

# By the Way

Linus doesn't mention it, but his new OS was going to be called _Freax_ at this point.
]]

---

## On Day 9658 (Feb 1st 2018)...

* 37-67% of _Web Servers_ run Linux (April 2017).<br>On the top 1,000,000 domains, it's 96%.
* Since November 2017, _all 500 fastest super-computers_ (TOP500 project) run Linux
* IBM runs Linux on _Mainframes_ (System z), marketshare ~28% (December 2008)
* 70% of _Mobile Devices_ run Linux (Android, December 2017)
* 29% of _Embedded Devices_ run Linux (Android and others, March 2012)

--

In all those groups there are large percentages of other Unix-like systems that are not Linux (macOS, iOS, BSD, PlayStation, QNX...)

--

And finally:

* 2% of _Desktop and Laptop machines_ run Linux (December 2017)

---

## Amazing Scale and Diversity

* ~30 supported Processor Platforms
* An individual kernel release has > 1000 contributors, ~10000 patches, changing ~3500 lines of code per day.
* Latest kernels have > 20M lines of code. Also several hundred swear words. :)

--

This is not from the Linux kernel, but funny anyway :)

```
// you can't fix this, but please increment the counter
// below if you try.
// hours wasted here: 56
```

---

## So what have we got?

* Linux is the _kernel_, though the project also includes _drivers_, _filesystems_ and other components
* Other parties maintain drivers, _system components_ and _application software_
  * Independent system components: _shell tools_, _graphical display servers_, _package management_, ...
* Yet others create _distributions_, with _installers_, _releases_, _updates_ and _support lifecycles_
  * Some distributions offer _commercial SLAs_
* Sometimes Linux is _integrated_ elsewhere, for instance in embedded systems, or in Windows
* Sometimes Linux is _derived from_, e.g. with Android

---

## As a .NET Dev, why should I give a \_?

* It's a _great deployment platform_

  * Fast
  * Performant
  * Scaleable
  * Free of license cost

* It's an _enthusiast/advanced user platform_

* It's small. It's big. It's stable. It boots fast. It's consistent. It's versatile. It's standardized. It's customizable.

--

* _It's a platform that does exactly what .eem[I] want._

---

## Getting Started

---

## Content slide

* Arghbargh

Use this to include images:

.svg-light[
![Creating a New Row with CQRS/Event Sourcing](es-create-new-row.svg)
]

Alternatively:

* .svg (no light background)
* .svg-width (no light background, size to width instead of height)
* .svg-light-width (size to width instead of height)

---

## Sources

* This presentation:

  * https://oliversturm.github.io/cqrs-event-sourcing
  * PDF download: https://oliversturm.github.io/cqrs-event-sourcing/slides.pdf

* Demo code:

  * https://github.com/oliversturm/cqrs-grid-demo (check _event-sourcing_ branch)

* Talk to Seneca

  * https://github.com/oliversturm/talk-to-seneca

---

class: impact

# Thank You

Please feel free to contact me about the content anytime.

.title-oli[
Oliver Sturm &bull; @olivers &bull; oliver@oliversturm.com
]

.title-logo[
<img src="template/devexpress.png" id="devexpress" alt="DevExpress"><img src="template/mvp.png" id="mvp" alt="MVP">
]
