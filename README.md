The Nikola website
==================

This is the Nikola website.

Live page: <https://getnikola.com/>

Update instructions (for maintainers)
-------------------------------------

1. In Nikola’s repo: run `scripts/set_version.py`.
2. Copy all documentation (`docs/*.{rst,txt}`), `AUTHORS.txt` and `CHANGES.txt`
   from the `nikola` repo to `stories/`.
3. Run `scripts/generate_conf.py` in Nikola’s repo and redirect its output to
   `listings/conf.py`.
4. Modify the version number in `stories/conf.txt`.

**Note**: do not edit documentation files here! See 2. above.
