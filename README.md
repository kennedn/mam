# mam

A Bash client for searching MyAnonamouse and downloading torrent files from the terminal. Searches titles, authors and narrators, with an interactive `fzf` picker for selecting one or more results.

## Prerequisites

- Bash, `curl`, `jq`, `fzf` and `column`
- Standard Unix utilities (`awk`, `basename`, `mktemp` and `wc`)
- A MyAnonamouse account with a valid `mam_id` API cookie

## Setup

Clone the repository:

```bash
git clone https://github.com/kennedn/mam.git
cd mam
```

Set your API cookie:

```bash
export MAM_ID='your_mam_id'
```

Alternatively, install and configure `rbw`, then store the cookie in the `mam_id (API)` field of a `myanonamouse.net` entry in your Bitwarden vault. When `MAM_ID` is unset or empty, the script retrieves it from your unlocked vault using `rbw`.

## Usage

```text
usage: mam [OPTION] [TERM]...
```

Search audiobooks (the default):

```bash
./mam "The Fisherman"
```

Search e-books or limit results to freeleech:

```bash
./mam -e "The Fisherman"
./mam -f "The Fisherman"
```

| Option | Description |
| --- | --- |
| `-a`, `--audiobooks` | Search audiobooks (default) |
| `-e`, `--ebooks` | Search e-books |
| `-A`, `--all-categories` | Search all main categories |
| `-f`, `--freeleech` | Show only freeleech torrents |
| `-h`, `--help` | Print help |

Results show the freeleech status, seeders, size, category and title. Type to filter results, use `Tab` to select multiple entries, then press `Enter` to download. Press `Esc` to cancel.

Selected `.torrent` files are saved to the current working directory.
