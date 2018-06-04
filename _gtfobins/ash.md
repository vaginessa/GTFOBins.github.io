---
functions:
  execute-interactive:
    examples:
      - code: |
          ash
    features:
      - sudo-enabled
      - suid-enabled
  file-write:
    examples:
      - code: |
          export LFILE=file_to_write
          ash -c 'echo data > $LFILE'
    features:
      - sudo-enabled
      - suid-enabled
---
