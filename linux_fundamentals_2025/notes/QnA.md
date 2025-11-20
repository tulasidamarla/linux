what is the difference between /usr and /bin

| Feature  | `/bin`                       | `/usr/bin`                          |
| -------- | ---------------------------- | ----------------------------------- |
| Purpose  | Essential for boot & repair  | Non-essential user utilities        |
| Mounting | Part of root (`/`) partition | Can be separate, might be unmounted |
| Used in  | Single-user mode, recovery   | Normal multi-user mode              |
| Examples | `ls`, `cp`, `sh`, `mkdir`    | `vim`, `perl`, `gcc`, `git`         |
