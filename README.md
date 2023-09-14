# Maunium sticker picker
A fast and simple Matrix sticker picker widget. Tested on Element Web, Android & iOS.

## Adding sticker pack
I know, there is an instruction below, but it didn't work for 100% for me, so I'll add how I did it.

I would prefer if the changes would be made on a new branch, in case several people are creating sticker packs at the same time resulting in a conflict inside `web/packs/index.json`.

Firstly, go into project folder and create a Python virtual environment
```sh
python -m venv .venv
```
Due to it working in nushell without an additional package I wasn't bothered testing yet, change the shell to bash or zsh and activate the virtual environment.
Then the project can be build using `pip` (As a note, without using a venv, pip would try to install this project as a system package)
```sh
zsh
source .venv/bin/activate
pip install .
```
Now, you can finally add sticker packs. For that, you need to create a new directory stating the name of the sticker pack, then simply put the png-files inside the directory (And the working directory is totally not cluttered when you have several sticker packs).
Then, you can create the pack using following command
```sh
sticker-pack <Pack Name> --add-to-index web/packs
```
While running the command for the first time, it will ask for your homeserver and access token. Those can be found on Element by going to Settings -> Help & About -> Advanced.

Now, the stickers are uploaded to your homeserver, all you need to do is to push the changes made in `web/packs`
```sh
git add web/packs
git commit
```
All what needs to be done is merging your branch to `master` (apologises for not calling it `mistress`, am mirroring maunium's repo) and the stickers should be visible after reloading element. In case for further questions, you feel free to ask.

## Discussion
Matrix room: [`#stickerpicker:maunium.net`](https://matrix.to/#/#stickerpicker:maunium.net)

## Instructions
For setup and usage instructions, please visit the [wiki](https://github.com/maunium/stickerpicker/wiki):

* [Creating packs](https://github.com/maunium/stickerpicker/wiki/Creating-packs)
* [Enabling the widget](https://github.com/maunium/stickerpicker/wiki/Enabling-the-widget)
* [Hosting on GitHub pages](https://github.com/maunium/stickerpicker/wiki/Hosting-on-GitHub-pages)

If you prefer video tutorials, [Brodie Robertson](https://www.youtube.com/c/BrodieRobertson) has made a great video on setting up the picker and creating some packs: https://youtu.be/Yz3H6KJTEI0.

## Comparison with other sticker pickers

* Scalar is the default integration manager in Element, which can't be self-hosted and only supports predefined sticker packs.
* [Dimension](https://github.com/turt2live/matrix-dimension) is an alternate integration manager. It can be self-hosted, but it's more difficult than Maunium sticker picker.
* Maunium sticker picker is just a sticker picker rather than a full integration manager. It's much simpler than integration managers, but currently has to be set up manually per-user.

| Feature                         | Scalar | Dimension | Maunium sticker picker |
|---------------------------------|--------|-----------|------------------------|
| Free software                   | ❌     | ✔️        | ✔️                     |
| Custom sticker packs            | ❌     | ✔️        | ✔️                     |
| Telegram import                 | ❌     | ✔️        | ✔️                     |
| Works on Element mobiles        | ✔️     | ❌        | ✔️                     |
| Easy multi-user setup           | ✔️     | ✔️        | ❌<sup>[#7][#7]</sup>  |
| Frequently used stickers at top | ❌     | ❌        | ✔️                     |

[#7]: https://github.com/maunium/stickerpicker/issues/7

## Preview
### Element Web
![Element Web](preview-element-web.png)

### Element Android
![Element Android](preview-element-android.png)

### Element iOS (dark theme)
![Element iOS](preview-element-ios.png)
