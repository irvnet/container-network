

# Content Publishing


## Objective: 
The project needs a publishing platform that provides features for content creation, but mostly to make it easy to make content available publicly with a minimum of effort.


[Gitbook](https://www.gitbook.com/) seems to be a great tool to handle real publishing of content that starts as simple markdown documents in git that need to be dressed up before releasing. It saves the trouble of having to set up even more infrastructure to be able to write simple tutorials (like wordpress or your pick of static site generators).

- Lots of great templates to get started
  - mostly interestd in the 'step by step instructions' template as a starting point
- Very easy to use the built in editor with few enough options that they aren't a distraction
- Really nice feature to allow embedded videos
  - upload videos to Youtube (unlimited space)
- bidirectional sync to a github repo
  - can only sync one github repo per space
  - considering using one space per tutorial (can do one way uploads keeping github as the golden source)

Next Steps:
- publish the first sample (yo-deploy, or test-deploy w/ nginx) as an experiment
- need to test how to sync a repo and a gitbook project to determine if all the samples live in one repo


### Tutorial Structure

A proposed structure for each document is:
- Introduction
- Objective
- Activities
- Prerequisites - what software needs to be installed
- Implementation - step by step instructions for the topic of discussion
- Cleanup - describe how to delete all the resources so readers don't get charged
- Demo (max 10m)
- Slides (using slides.com / reveal.js for decks)

Multi-part tutorials:
- part 1 gets published publicly
- part 2 & 3 are for public or customer-facing sessions
- part 1 gets pushed (manually) from local machine as markdown to gitbook (remainder stays in git)




## keep 2 gitbook respos (or spaces)
- private - where draft and backlog content get screated
- public - wehre content gets released when appropriate for all to see
This allows me to separate the pace of building vs releasing content



### Video Demos
Keep it simple
- capture them with quicktime
- post to Daily Motion or Vimeo
- consider turning them into short animated gifs for very short (under 2 min) demos

---

## Resources (Publishing)

### Great format for document structure
https://kumorilabs.com/blog/k8s-3-create-deployments-services-kubernetes/

### Style Guide for kubernetes documentation
https://kubernetes.io/docs/contribute/style/style-guide/

### comparisons of youtube, daily motion, vimeo (proposing daily motion)
https://videoconverter.wondershare.com/vimeo/vimeo-dailymotion.html

### animated gif software (proposing Gify Capture)
https://www.igeeksblog.com/best-mac-apps-to-create-gif/
https://www.digitaltrends.com/computing/best-gif-maker-apps/





