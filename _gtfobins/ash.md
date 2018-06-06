---
functions:
  execute:
    features:
      - sudo-enabled
      - suid-enabled
      - interactive
    examples:
      - code: BINARY
  file-write:
    features:
      - sudo-enabled
      - suid-enabled
    examples:
      - code: |
          export LFILE=file_to_write
          BINARY -c 'echo data > $LFILE'
---
