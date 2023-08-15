# Stone Cold PostgreSQL

I'm working on postgres integration for stone cold sql

## Timebox

I'd like to give myself a week to do this. It feels aggressive, but I don't think I have too much going on in terms of extracurricular's.

## Journey

So far, I've modified the parser file at `gram.y` adding `WHAT` as a `reserved_keyword` and as a `bare_label_keyword`.

## Plan

- Create environment
- Develop Syntax Replacement
- Create plan for making changes
- Test Changes

### Syntax Replacement

- Postgres has docs on their key words:
  - [SQL Syntax Overview](https://www.postgresql.org/docs/current/sql-syntax-lexical.html#SQL-SYNTAX-IDENTIFIERS)
  - [Appendix C - SQL Key Words](https://www.postgresql.org/docs/current/sql-keywords-appendix.html)
    - I captured this table in [google docs](https://docs.google.com/spreadsheets/d/1XW2RhBAQzmxkdNBtkhpnLqkRFdJ8s7L3KgDRQqO3hTk/edit?usp=sharing)

- There are reserved and non-reserved key words
  - reserved key words are never allowed as identifiers
  - non-reserved key words can (and so aren't really key), but have some predefined meaning in some contexts

- Parser sees things a little more complicated, as there are several classes of key words

#### Should I have multiple words for some key words?

Stone cold promos feature a lot of phrases that would be hard to replicate if I replaced key word for key word. So, I'm thinking about the feasibility of substituting multiple words (not via _), but using whitespace to make it look more natural (and probably less user friendly)

### Setup

- Will be using a version of postgres pulled directly from the master/main branch
- Compile it using WSL Debian
- Test via installing postgres to WSL Debian

#### Installing Postgres

Taking note of the installation process in [Chapter 19](https://www.postgresql.org/docs/15/runtime.html).

##### WSL

Building and installing seems to work using WSL by first satisfying all postgres dependencies using the package manager. In debian wsl, I used `apt-get build-dep postgresql` to first satisfy all dependencies, and then I cloned postgres directly from the git repo.

##### Debian Native

I've verified that I can build and install from source on Debian native as well. I haven't used the exact same process as WSL, but I hope to for reproducibility.
