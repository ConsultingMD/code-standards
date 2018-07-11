# Configuration

In your repo, add the following to your `.codeclimate.yml`:

```
prepare:
  fetch:
  - url: "https://raw.githubusercontent.com/ConsultingMD/code-standards/master/java/codeclimate_checkstyle.xml"
    path: "checkstyle.xml"

plugins:
  checkstyle:
    enabled: true
    config:
      file: "checkstyle.xml"

```
