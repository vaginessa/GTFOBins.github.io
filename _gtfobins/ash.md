---
functions:
  execute:
    examples:
      - code: |
          ash
    features:
      - sudo-enabled
      - suid-enabled
      - interactive
  file-write:
    examples:
      - code: |
          export LFILE=file_to_write
          ash -c 'echo data > $LFILE'
    features:
      - sudo-enabled
      - suid-enabled
---
