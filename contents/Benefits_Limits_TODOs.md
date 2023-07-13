# Benefits of adopting KPA / 1

There are several benefits using KPA:

- **Concentrate just on the contents**: once you have defined your project, you
  don't need to care about anything but writing **KP**s.
  No need to manually syntax highlight your code blocks, no need to adapt text,
  no need to duplicate your slide to modify just a simple sentence. Just write
  your **KP**s in markdown and you're good to go.

- **Compose training and presentations dynamically**: no more Power Point slides
  cut and paste. You can combine your **KP**s in the way that fits your needs,
  creating as many variants of your training and presentations as you need.

---

## Benefits of adopting KPA / 2

- **Have the same look & feel for every training or presentation**: no more "Ok,
  now you need to apply this new slide format to all our 100 presentations".
  You will define your project look & feel one time and it will be applied
  everywhere, always the same way.

- **Use a standard and reusable format**: the same documentation you will produce
  with KPA could be used wherever you want because it's Markdown, which is a
  standard, and you will be able to write your own tool to manage your **KP**s.

---

## Benefits of adopting KPA / 3

- **Keep everything versioned and in order**: once you'll store your **KPA**
  projects in a Git repository, you'll get versioning, monitoring of the changes
  and your entire knowledge in one traceable place.

- **Let everyone do their job**: markdown is simple to the point that even
  non-technical people can edit Knowledge Pods and this allows for everyone to
  do their job: graphics can work on the themes, instructors can write the
  contents and you, the **KPA master ©**, will put everything together.

---

## Limits

There are certain limits using the [Marp ecosystem](https://marp.app/#get-started) that require a bit of
knowledge on stylesheets and CSS, **like when you need to place more than one
image in your slide**, but in the end, it's just a matter of setting up the css
theme.

Another limit is the fact that using KPA you **can't see your changes live**, you
will always need to launch the container to generate your files. A way to avoid
this is to use the [Visual Studio Code Marp Plugin](https://github.com/mmul-it/kpa/blob/main/Commands.md#themes) that will make previews
live.

---

## TODOs

Every **KPA** issue is tracked in the [KPA GitHub Page](https://github.com/mmul-it/kpa/issues), so you can suggest and propose
there improvements.

There are at least two main issues that will be addressed sooner than later: 

- **The size of the KPA container** that today is big and by adding more layers
  could be sensively reduced.
- **Support for book generation over KPs** so that the slides can become A4
  books. This will be a cobination of Pandoc and Markdown rendering.
