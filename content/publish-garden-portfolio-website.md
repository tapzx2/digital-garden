---
tags:
  - public
source:
---

- [best ways to self publish from reddit and ceo](https://www.reddit.com/r/ObsidianMD/comments/16e5jek/best_way_to_selfhost_obsidian_publish/)
- [quartz](https://quartz.jzhao.xyz/authoring-content)
	- [video walk through of quartz](https://www.youtube.com/watch?v=6s6DT1yN4dw)
	- [adjustment to publishing with quartz for maximum efficiency ](https://oliverfalvai.com/evergreen/my-quartz-+-obsidian-note-publishing-setup)
## Log
[[2024-08-08]] Working on media links. Oops! Unending loop on @RyanMarin file. Because self-linked. Since scanning whole vault, no recursion is needed.
[[2024-08-06]] Unsure about customizing technology I know little about or if help will arrive. Attempting to use quartz in normal way, but writing terminal script to copy files tagged `public` to quartz to automate process. Script works. Updates needed: 
- alerts on linked files that aren't public
- fix search, copy, and linking of media files
- set grep search to `- public` instead of just `public`. An author or source name may have that. Or location.
Question:
- how to share code? not markdown and not front-matter. does quartz support this?

[[2024-08-05]] joined discord group, made contact with Oliver. He offered suggestions. Didn't work. Wrote detailed question to clarify.

[[2024-08-04]] issue with blending github publish and maximum efficiency work. Private messaged Oliver on [Mastodon](https://mastodon.social/@tapianicholas)

[[2024-08-03]] Started research and work.
## Resources
quick git refresher: https://rogerdudler.github.io/git-guide/

## Process Test and Attempt for Continuous Integration

when updating, from `quartz` folder run:
`npx quartz sync --directory=../digital-garden`

when local testing run:
`npx quartz build --directory=../digital-garden --serve`

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