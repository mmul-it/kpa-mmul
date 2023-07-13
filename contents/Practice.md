# How to create a **KPA** project

A **KPA** project should have a structure like the [example project](https://github.com/mmul-it/kpa/tree/main/projects/example)
or like the [kpa-mmul project](https://github.com/mmul-it/kpa-mmul) in its dedicated repo, both on GitHub:

```console
projects/kpa-mmul/
├── common
│   ├── settings.yml
│   ├── mmul.tex
│   └── theme.css
├── images
│   ├── slide-background.png
│   └── ...
├── templates
│   ├── chapter.md.j2
│   └── cover.md.j2
├── contents
│   ├── Basics.md
│   └── ...
└── KPA.yml
```

Two files are mandatorty: `common/settings.yml` and `KPA.yml`.

---

## The **KPA** project settings

The `common/settings.yml` contains the general parameters that will define how
the documents will be produced, overriding the Ansible roles defaults:

```yaml
kpa_project_dir: "projects/mmul"

# Pandoc (agenda) section
pandoc_agenda_template_file: "{{ kpa_project_dir }}/common/mmul.tex"
pandoc_agenda_background_image: "{{ kpa_project_dir }}/images/schedule-background.png"

# Marp (slides) section
marp_theme: mmul
marp_paginate: true
marp_theme_file: "{{ kpa_project_dir }}/common/theme.css"
marp_background_image: "{{ kpa_project_dir }}/images/slide-background.png"
marp_cover_template: "{{ kpa_project_dir }}/templates/cover.md.j2"
marp_cover_background_image: "{{ kpa_project_dir }}/images/cover-background.png"
marp_chapter_template: "{{ kpa_project_dir }}/templates/chapter.md.j2"
marp_chapter_background_image: "{{ kpa_project_dir }}/images/chapter-background.png"
```

This will never change for the project, since contains all the style indications.

---

## The **KPA** project document / 1

The first part of the `KPA.yml` contains the document composition, with the names
of the generated files, and information abut the author, copyright and else:

```yaml
output_file: "output/KPA"
pandoc_agenda_output_markdown: "{{ output_file }}.agenda.md"
pandoc_agenda_output_pdf: "{{ output_file }}.agenda.pdf"
marp_output_markdown: "{{ output_file }}.md"
marp_output_pdf: "{{ output_file }}.pdf"

marp_title: "Knowledge **Pods** Approach"
marp_subtitle: "Share knowlege in a standard, dynamic and open-souce way"

marp_author: 'Raoul Scarazzini'
marp_copyright: '© 2023 MiaMammaUsaLinux.org'
marp_cover_logo: "{{ kpa_project_dir }}/images/kpa-logo-80-gray.svg"
```

---

## The **KPA** project document / 2

The second part of the `KPA.yml` contains the slide set declaration that will
combine the various **KP**s:

```yaml
kpa_contents: "{{ kpa_project_dir }}/contents"

marp_slides:
  - cover: true
    title: "{{ marp_title }}"
    subtitle: "Knowledge Pods Approach"
  - chapter: 'Basics'
    title: 'What is KPA?'
    content: "{{ kpa_contents }}/Basics.md"
  - chapter: 'Practice'
    title: 'Using KPA'
    content: "{{ kpa_contents }}/Practice.md"
    ...
    ...
```

---

## Executing the **KPA** container

Once everything is in place one can just use the **KPA container** to generate
the two documents, so the slide set and the agenda:

```console
> docker run --rm \
    -v $HOME/kpa-mmul:/kpa/projects/mmul \
    -v /tmp:/kpa/output \
    quay.io/mmul/kpa -p mmul -y KPA.yml
```

The container run will:

- Map the project dir as a volume inside the `/kpa/projects/<project name>` container's dir.
- Map the output directory (here `/tmp`) inside the `/kpa/output` container's directory.
- Pass the `--project mmul` and `--yml KPA.yml` parameters that the executable expects.

---

## Getting the **KPA** results

The generated files will be available in the output directory, and will usually
be two couples of files. In this case:

```console
> ls -1 /tmp/KPA.*
/tmp/KPA.agenda.md
/tmp/KPA.agenda.pdf
/tmp/KPA.md
/tmp/KPA.pdf
```

Every change made on the local files will be reflected in the generated files,
making this approach suitable for automated stuff, like CI pipelines, in a
real-life example of **Knowledge As A Service**.

---

## KPA Lab 1

A local modification and document generation, very coooool!

---

## KPA Lab 2

A GitHub Actions pipeline automatic doc generation, using the [kpa-mmul](https://github.com/mmul-it/kpa-mmul) project.
