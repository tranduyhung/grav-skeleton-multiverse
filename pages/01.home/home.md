---
title: Multiverse
images:
    -
        thumbnail: 01.jpg
        title: Magna feugiat lorem
        description: Nunc blandit nisi ligula magna sodales lectus elementum non. Integer id venenatis velit.
    -
        thumbnail: 02.jpg
        title: Nisl adipiscing
        description: Nunc blandit nisi ligula magna sodales lectus elementum non. Integer id venenatis velit.
    -
        thumbnail: 03.jpg
        title: Tempus aliquam veroeros
        description: Nunc blandit nisi ligula magna sodales lectus elementum non. Integer id venenatis velit.
    -
        thumbnail: 04.jpg
        title: Aliquam ipsum sed dolore
        description: Nunc blandit nisi ligula magna sodales lectus elementum non. Integer id venenatis velit.
    -
        thumbnail: 05.jpg
        title: Cursis aliquam nisl
        description: Nunc blandit nisi ligula magna sodales lectus elementum non. Integer id venenatis velit.
    -
        thumbnail: 06.jpg
        title: Sed consequat phasellus
        description: Nunc blandit nisi ligula magna sodales lectus elementum non. Integer id venenatis velit.
    -
        thumbnail: 07.jpg
        title: Mauris id tellus arcu
        description: Nunc blandit nisi ligula magna sodales lectus elementum non. Integer id venenatis velit.
    -
        thumbnail: 08.jpg
        title: Nunc vehicula id nulla
        description: Nunc blandit nisi ligula magna sodales lectus elementum non. Integer id venenatis velit.
    -
        thumbnail: 09.jpg
        title: Neque et faucibus viverra
        description: Nunc blandit nisi ligula magna sodales lectus elementum non. Integer id venenatis velit.
    -
        thumbnail: 10.jpg
        title: Mattis ante fermentum
        description: Nunc blandit nisi ligula magna sodales lectus elementum non. Integer id venenatis velit.
    -
        thumbnail: 11.jpg
        title: Sed ac elementum arcu
        description: Nunc blandit nisi ligula magna sodales lectus elementum non. Integer id venenatis velit.
    -
        thumbnail: 12.jpg
        title: Vehicula id nulla dignissim
        description: Nunc blandit nisi ligula magna sodales lectus elementum non. Integer id venenatis velit.

form:
    action: /home
    name: contact-form
    fields:
        - name: name
          label: Name
          placeholder: Name
          type: text
          validate:
            required: true
        - name: email
          label: Email
          placeholder: Email
          type: email
          validate:
            required: true
        - name: message
          label: Message
          placeholder: Message
          type: textarea
          rows: 4
          validate:
            required: true
    buttons:
        - type: submit
          value: Send
          classes: special
        - type: reset
          value: Reset
    process:
        - email:
            from: "{{ config.plugins.email.from }}"
            to:
              - "{{ config.plugins.email.from }}"
            subject: "[Contact] Message from {{ form.value.name|e }}"
            body: "{% include 'forms/data.html.twig' %}"
        - save:
            fileprefix: contact-
            dateformat: Ymd-His-u
            extension: txt
            body: "{% include 'forms/data.txt.twig' %}"
        - display: thank-you
---
