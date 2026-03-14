# Custom "Glorious Engrammer" keymap for MoErgo Glove80

Personal customization of the [*Glorious Engrammer*](https://sunaku.github.io/moergo-glove80-keyboard.html#layers) keymap, a fantastic project by Suraj Kurapati (sunaku).  Full documentation and setup instructions are available in the upstream [README](https://github.com/sunaku/glove80-keymaps/blob/main/README.md).

## Updating

Use `custom-next` for rebases. Keep `custom` public and never force-push it.
Merge `custom-next` into `custom` with a regular merge commit.

One-time setup:

```sh
git switch custom
git switch -c custom-next
git push -u origin custom-next
```

```sh
tag=v42
upstream_tag=upstream-$tag
custom_tag=custom-$tag

git switch custom-next
git fetch upstream --tags

git tag -a "$upstream_tag" "$tag" -m "Upstream $tag snapshot"
git rebase "$tag"

git push --force-with-lease -u origin custom-next

git switch custom
git merge --no-ff custom-next
git tag -a "$custom_tag" -m "Custom merged from custom-next on $tag"

git push origin custom
git push origin "refs/tags/$upstream_tag" "refs/tags/$custom_tag"
```
