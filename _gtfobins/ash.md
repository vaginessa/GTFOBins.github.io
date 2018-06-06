---
functions:
  execute:
    examples:
      - code: BINARY
    features:
      - sudo-enabled
      - suid-enabled
      - interactive

  file-write:
    examples:
      - code: |
          export LFILE=file_to_write
          BINARY -c 'echo data > $LFILE'
    features:
      - sudo-enabled
      - suid-enabled
---
