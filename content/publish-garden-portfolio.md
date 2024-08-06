---
tags:
  - shag
  - public
  - video
source:
  - "[[@Fine Home Building]]"
---

- [best ways to self publish from reddit and ceo](https://www.reddit.com/r/ObsidianMD/comments/16e5jek/best_way_to_selfhost_obsidian_publish/)
- [quartz](https://quartz.jzhao.xyz/authoring-content)
	- [video walk through of quartz](https://www.youtube.com/watch?v=6s6DT1yN4dw)
	- [adjustment to publishing with quartz for maximum efficiency ](https://oliverfalvai.com/evergreen/my-quartz-+-obsidian-note-publishing-setup)
- 

when updating, from `quartz` folder run:
`npx quartz sync --directory=../digital-garden`

when local testing run:
`npx quartz build --directory=../digital-garden --serve`

## Log
[[2024-08-04]] issue with blending github publish and maximum efficiency work. Private messaged Oliver on [Mastodon](https://mastodon.social/@tapianicholas)

## Resources
quick git refresher: https://rogerdudler.github.io/git-guide/

## Process
local test no problem.
`npx quartz build --directory=../digital-garden --serve
- works great locally!

from terminal with standard .yml file from install docs
`npx quartz sync --directory=../digital-garden`
- This builds a blank quartz instance in github pages.

Update .yml file to:
`npx quartz build --directory=../digital-garden`
rerun:
`npx quartz sync --directory=../digital-garden`
- This builds a broken quartz instance in github pages.

Test "normal" workflow. Make obsidian vault the `content` directory. Add content.
Update .yml file to:
`npx quartz build`
run:
`npx quartz build`
`npx quartz sync`
- this works just fine, but doesn't follow Oliver's process.
## Question and Understanding

IF I understand correctly, the file structure locally for Oliver's system is supposed to be
```
folder/
    digital-garden/
        obisidan-files-and-folders.md
	quartz/
		.git/
	    .git-stuff/
	    content/
		public/
		    this-is.xml
		    what.html
		    quartz.js
		    builds.css
		quartz/
```

This works great locally.

After sending the stuffs to github, the directory structure looks like this.

```
quartz/
	.git-stuff/
	content/
	public/
		this-is.xml
		what.html
		quartz.js
		builds.css
	quartz/
```

So, when the github pages server runs the `npx quartz build --directory=../digital-garden` command from the .yml file, it doesn't work. There's obviously no digial-garden directory to build from. I made the git repo inside the quartz folder. Pushing my whole vault to a public github repo wouldn't make sense. So, how do I make this work with your workflow?

Side question for my understanding, why is the github pages server being instructed to build quartz again? It seems like all of the needed files are in `public` directory.