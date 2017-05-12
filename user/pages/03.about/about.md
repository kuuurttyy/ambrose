---
content: "Lorem ipsum dolor sit amet, consectetur adipiscing elit. Nullam pharetra arcu sapien. Sed mattis consectetur rhoncus. Curabitur faucibus dui ac justo convallis bibendum. Aenean vitae enim odio. Donec egestas mattis leo. Quisque id lacus vitae elit mattis venenatis imperdiet eu orci. Nam facilisis porta fermentum.\r\n\r\nEtiam egestas ultrices sem, at efficitur odio semper in. Vestibulum egestas sed turpis non viverra. Donec sed libero auctor, imperdiet lectus non, dapibus sapien. Cras vel dapibus felis. Nunc ac augue ligula. Cras nec posuere dolor, a ultrices mauris. Nunc cursus tellus sed vestibulum venenatis. Nunc molestie magna metus, non porttitor nibh pellentesque vel. Sed facilisis porta dolor ut maximus. Integer massa tortor, consequat rhoncus cursus eu, vestibulum a nisl. Quisque suscipit sed odio at laoreet. Proin dapibus diam magna, eu blandit erat interdum id. Aliquam et neque id dui interdum semper. Maecenas vitae augue mi. Vestibulum pretium odio ut quam vulputate vehicula."
image:
    user/themes/ambrose/assets/about/sZte2LhvXDBN0QH.JPG:
        name: sZte2LhvXDBN0QH.JPG
        type: image/jpeg
        size: 780399
        path: user/themes/ambrose/assets/about/sZte2LhvXDBN0QH.JPG
title: About
order_by: ''
order_manual: ''

form:
    name: contact

    fields:
        - name: name
          label: Name
          placeholder: Enter your name
          autofocus: on
          autocomplete: on
          type: text
          validate:
            required: true

        - name: email
          label: Email
          placeholder: Enter your email address
          type: email
          validate:
            required: true

        - name: message
          label: Message
          placeholder: Enter your message
          type: textarea
          validate:
            required: true


    buttons:
        - type: submit
          value: Submit
        - type: reset
          value: Reset

    process:
        - email:
            from: "{{ config.plugins.email.from }}"
            to: "{{ config.plugins.email.to }}"
            subject: "[Site Contact Form] {{ form.value.name|e }}"
            body: "{% include 'forms/data.html.twig' %}"
        - save:
            fileprefix: contact-
            dateformat: Ymd-His-u
            extension: txt
            body: "{% include 'forms/data.txt.twig' %}"
        - message: Thank you for getting in touch!
        - display: thankyou
---

