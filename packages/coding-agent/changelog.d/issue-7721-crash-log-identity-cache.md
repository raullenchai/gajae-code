### Improved

- Crash index compaction no longer re-reads and re-parses the entire gjc-crash.log on every session start when the log is unchanged. The compactor now caches the log's identity (size, modification time, and inode on POSIX systems) in the index. On subsequent compactions with no new journal events, the log is skipped if its identity matches, saving 2–3 seconds on session startup for typical ~300 KB logs. ([#7721](https://github.com/Yeachan-Heo/gajae-code/issues/7721))
