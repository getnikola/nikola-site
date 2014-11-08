The Nikola website
==================

This is the Nikola website.

Live page: <http://getnikola.com/>

Update instructions (for maintainers)
-------------------------------------

1. In Nikola’s repo: run `scripts/set_version.py`.
2. Copy all documentation and `CHANGES.txt` to `stories/`.
3. Run `scripts/generate_conf.py` in Nikola’s repo and redirect its output to
   `listings/conf.py`.
4. Modify the version numbers in `stories/welcome.txt` and `stories/conf.txt`.
