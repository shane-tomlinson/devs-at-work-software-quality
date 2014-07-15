We write a lot of software at Mozilla. Some of the software is superb, some could use a rewrite. It's difficult to write software that "works". It's even more difficult to write software that works AND could be considered high quality.

I have spent my entire professional career trying to craft high quality software, and I still struggle. I look back at code that I wrote as little as six months ago and go WTF? I know that I have a lot to learn. Luckily, I am part of an amazing community that has a lot to teach. The Mozilla community builds amazing projects like MDN, Firefox and FirefoxOS; projects that are complex, huge in scope, developed over many years, and require the effort of thousands. These projects are only successful because of the skill of their participants.

Over the past couple of months, several community members have agreed to share their thoughts on the question "How can we, as developers, write more superb software?" This is the first of a series of interviews where I take on the role of an apprentice to learn from some of Mozilla's finest.

Since shipping software to millions of people involves more than just writing code, the interviews cross functional lines. Folks from QA, Security and development have all been interviewed, and I hope to cover additional areas in the future.

The target audience is anybody who writes software, regardless of the preferred language or level of experience. If you are reading this, you are part of the part of the target audience! I ask the interviewees high level questions that can be applied to any language, often the questions are about processes and tooling.

The conversations are free-flowing, but I have several specific questions that I am trying to here about:

* How do other developers approach writing high quality, maintainable software?
* What does "high quality, maintainable software" even mean?
* What are my peers looking for when doing code review?
* How does development/Security/QA fit together to support each other's efforts?
* What matters to Security? What do they look for when doing a security review/audit?
* What matters to QA? What do they look for before signing off on a release?
* What tools are people using?
* What can *I* do, as a developer, to write great software and facilitate the entire process?

I will present the highlights of one or two interviews per article. Each interview will contain a short introduction to the person being interviewed followed by a series of questions and answers.

Where an interview's audio was recorded, I will provide a link to the full transcript. If the interview was done over email, I will link to the contents of the original email.

Now, on to the first interview!


The first interview is with Fernando Jimenez Moreno, a FirefoxOS developer from Telefonica. I had the opportunity to work with Fernando last autumn when we integrated Firefox Accounts into First Time Experience of FirefoxOS. I was impressed not only with Fernando's technical prowess, but also his ability to bring together the employees of three companies in six countries on two continents to work towards a common goal.

Fernando talks about how Telefonica became involved in FirefoxOS, how to bring a disparate group together, common standards, code reviews, and above all, being pragmatic.



> S: What do you and your team at Telefonica do?

> F: I'm part of what we call the platform team. We have different teams at Telefonica, one is focused on front end development in Gaia, and the other one is focused on the platform itself, like Gecko, Gonk and external services. We work in several parts of FirefoxOS, from Gecko to Gaia, to services like the SimplePush server. I've personally worked on things like the [RIL interface layer](https://developer.mozilla.org/en-US/Firefox_OS/Platform/Architecture), payments, applications API and other Web APIs, and almost always jump from Gecko to Gaia and back. Most recently, I started working on the [Loop project](https://wiki.mozilla.org/CloudServices/Loop), which is Telefonica and Mozilla's WebRTC service.

> S: How did Telefonica get involved working with Mozilla?

> F: Well, that's a longer story. We started working on a similar project to FirefoxOS, but instead of being based on Gecko, we were working with WebKit. So we were creating this open web device platform based on WebKit. When we heard about Mozilla doing the same with Gecko, we decided to contact you and started working on the same thing. Our previous implementation was based on a closed source port of WebKit and it was really hard to work that way. Since then, my day-to-day work is just like any other member of Telefonica's FirefoxOS team, which I believe is pretty much the same as any other Mozilla engineer working on B2G.

> S: You are known as a great architect, developer, and inter-company coordinator. For Firefox Accounts on FirefoxOS, you brought together people from Telefonica, Telenor, and Mozilla. What challenges are present when you have to work across three different companies?

> F: It has given me quite a challenge and experience, especially during the first days of FirefoxOS. We started working with Mozilla back in 2011, and it took some time for both companies to find a common work flow that fit well for both parts. I mean, we were coming from a telco culture where many things were closed and confidential by default, as opposed to the openness and transparency of Mozilla. For some of us coming from other open source projects, it wasn't that hard to start working in the open and to be ready to discuss and defend our work on public forums. But, for other members of the team it took some time to get used to that new way of working, and new way of presenting our work. Also, because we were following agile methodologies in Telefonica while Mozilla wasn't still doing it, we had to find this common workflow that suits both parts. It took some time to do it, a lot of management meetings, a lot of discussions about it. Regarding working with other telco companies, the experience has also been quite good so far, especially with Telenor. We still have to be careful about the information that we share with them, because at the end of the day, we are still competitors. But that doesn't mean we cannot work with them in a common target like what happened with Firefox Accounts.

> S: It sounds like when Mozilla and Telefonica were both starting out on this process, both sides had to change. Some people at Telefonica had to get used to working in the open, and some people at Mozilla had to change their methodologies. You mentioned agile in particular. How did you decide what common practices to use and how did you establish a common culture to get everybody to go together?

> F: I think for this agile methodology, we focused more on the front end parts because Gecko already had a very known process and a very known way of developing. It has its own train mechanism of 6 weeks. As I said, we have two different teams in Telefonica, the platform team and the front end team. The ones doing the most, the biggest effort of finding that common workflow were the front end team because we started working on Gaia and Gaia was a new project with no fixed methodologies. They tried to find the common methodology for Gaia. In the meantime, the people working on the task were trying to learn the Gecko process and also we are in the middle between working with the Gaia team and working with Gecko engineers. I don't know if we really found the workflow, the perfect workflow, but I think we are doing good. I mean we participate in agile methodologies, but when it turns out that we need to do Gecko development and we need to focus on that, we just do it their way.

> S: In a multidisciplinary, multi-company project, how important are common standards like style guides, tools, and processes to making a project succeed?

> F: Well, I believe when talking about software engineering, standards are very important in general. But, I don't care if you call it SCRUM or KANBAN or SCRUMBAN or whatever, or if you use Git workflow or Mercurial workflow, or if you use Google or Mozilla's Javascript style guide. But you totally need some common processes and standards, especially in large engineering groups like open source, or Mozilla development in general. When talking about this, the lines are very thin. It's quite easy to fail spending too much time defining and defending the usage of these standards and common processes and losing the focus on the real target. So, I think we shouldn't forget these are only tools, they are important, but they are only tools to help us, and help our managers. We should be smart enough to be flexible about them when needed. We do a lot of code reviews about code style, but in the end what you want is to land the patch and to fix the issue. If you have code style issues, I want you to fix them, but if you need to land the patch to make a train, land it and file a follow on bug to fix the issues, or maybe the reviewer can do it if they have the chance.

> S: Whenever new people come into the project, how can you go about educating them about the standards that already exist?

> F: I would say, at first, documentation. I guess reviews and day-to-day work, where people are already familiar with these standards participate in this education process. There are also tools like linters or git and mercurial hooks to enforce some of these standards.

> S: FirefoxOS code is Gonk, which is Linux basically, Gecko and Gaia. Each system is large, complex, and intimidating to a newcomer. You regularly submit patches to Gecko and Gaia. You had to learn about all of these systems somehow. Whenever you want to go dive into a project, how do you learn about the system you want to work in?

> F: I'm afraid there is no magic technique. What works for me might not work for others for sure. What I try to do is to read as much documentation as possible inside and outside of the code, if it's possible. I try to ask the owners of that code when needed, and also if that's possible, because sometimes they just don't work in the same code or they are not available. I try to avoid reading the code line by line at first and I always try to understand the big picture before digging into the specifics of the code. I think that along the years, you somehow develop this ability to identify patterns in the code and to identify common architectures that help you understand the software problems that you are facing.

> S: When you start coding in unfamiliar territory, how do you ensure your changes don't cause unintended side effects? Is testing a large part of this?

> F: Yeah, basically tests, tests and more tests. You need tests, smoke tests, black box tests, tests in general. Also at first, you depend a lot on what the reviewer said, and you trust that the reviewer, or you can ask QA or the reviewer to add tests to the patch.

> S: Let's flip this on its head and you are the reviewer and you are reviewing somebody's code. Again, do you rely on the tests whenever you say "OK, this code adds this functionality. How do we make sure it doesn't break something over there?"

> F: I usually test the patches that I have review if I think the patch can cause any regression. I also try to run the tests on the "try" server, or ask the developer to trigger a "try" run.

> S: OK, so tests.. A lot of tests.

> F: Yeah, now that we are starting to have good tests in FirefoxOS, we have to make use of them.

> S: I feel like there is this tension between what level of test to write. Some people say "unit tests are worthless because if the interface changes then you have to go update all the tests and functional tests are where it's at." And other people are like "nooo, you've gotta unit test everything and functional tests won't tell you where the problem is, it'll only tell you there is problem." I would love to write huge numbers of both, but sometimes there is not enough time. I don't know if that's a false assumption on my part. How do you deal with testing in time constrained situations? Do you try to do both functional tests and unit tests? If you had to ditch one, where do you focus your testing efforts?

> F: I guess it depends on the time that you have for the coding part. I usually approach it, I think the wrong way. I write the code then write the tests, when I should probably do the opposite. I think it's this urge to see something working. Because that's actually your job to make the patch work, and then you need to make sure it's well written and it works well and it doesn't break so you write the tests for it. I don't know which one I would choose, it depends on the patch and the time that I have. I also ask "what would the reviewer ask me to write?" I mean, we all love tests, and we would all like to write as many tests as possible, but in the end we have a lot of patches to write and we just want the patch to be landed. We need to make the reviewer happy, if he wants this test, I will write this test. That's it.

> S: What do you look for when you are doing a review?

> F: In general where I look first is correctness. I mean, the patch should actually fix the issue it was written for. And of course it shouldn't have collateral effects. It shouldn't introduce a regression.  And as I said, I try to test the patches myself if I have the time or if the patch is critical enough, to see how it works and to see if it introduces a regression. And also I look that the code is performant and is secure, and also if, I always try to ask for tests if I think they are possible to write for the patch. And I finally look for things like quality of the code in general, and documentation, coding style, contribution, process correctness. If you have to squash your commits for pushing it to Gaia, then well, you have to do it. Or if you have to write the commit message with the reviewer name, or the bug number, then you have to do it because it's the process for that project.

> S: Whenever you are reviewing code, say it's a large patch, would you prefer that patch be broken up into smaller commits that show the developer's process, or do you like to see one giant thousand line patch?

> F: I prefer it to be split between different commits. I usually actually write the code that way. I do different patches with different numbers for each patch, that way I think you can even ask for review of different reviewers for each different part because sometimes you will write for B2G but it also involves Gonk parts, or Gecko parts, or Gaia parts, and the same reviewer cannot review the whole stack, so you need to split it into different pieces.

> S: And then say, you did have one of these patches that was 3 different commits. Before that is merged, would you squash those into one commit and then merge it?

> F: I usually ask the developer to do it, to squash it, or sometimes they do it themselves.

> S: You reviewed one of my large patches to integrate Firefox Accounts into FirefoxOS. You placed much more of an emphasis on consistency than any review I have had. By far.

> F: Well it certainly helps with overall code quality. When I do reviews, I mark these kinds of comments as "nit:" which is quite common in Mozilla, meaning that "I would like to see that changed, but you still get my positive review if you don't change it, but I would really like to see them changed."

> S: Two part question. As a reviewer, how can you ensure that your comments are not taken too personally by the developer? The second part is, as a developer, how can you be sure that you don't take it too personally?

> F: For the record, I have received quite a few hard revisions myself. I never take them personally. I mean, I always try to take it, the reviews, as a positive learning experience. I know reviewers usually don't have a lot of time to, in their life, to do reviews. They also have to write code. So, they just quickly write "needs to be fixed" without spending too much time thinking about the nicest ways to say it. Reviewers only say things about negative things in your code, not negative, but things that they consider are not correct. But they don't usually say that the things that are correct in your code and I know that can be hard at first. But once you start doing it, you understand why they don't do that. I mean, you have your work to do. This is actually especially hard for me, being a non-native English speaker, because sometimes I try to express things in the nicest way possible but the lack of works make the review comments sound stronger than it was supposed to be. And, what I try to do is use a lot of smileys if possible. And always, I try to avoid the "r-" flag if I mean, the "r-" is really bad. I just clear it, use the "feedback +" or whatever.

> S: You already mentioned that you try to take it as a learning experience whenever you are developer. Do you use review as a potential teaching moment if you are the reviewer?

> F: Yeah, for sure. I mean just the simple fact of reviewing a patch is a teaching experience. You are telling the coder what you think is more correct. Sometimes there is a lack of theory and reasons behind the comments, but we should all do that, we should explain the reasons and try to make the process as good as possible.

> S: Do you have a snippet of code, from you or anybody else, that you think is particularly elegant that others could learn from?

> F: I am pretty critical with my own code so I can't really think about a snippet of code of my own that I am particularly proud enough to show :). But if I have to choose a quick example I was quite happy with the result of the last big refactor of the [call log database](https://github.com/mozilla-b2g/gaia/blob/master/apps/communications/dialer/js/call_log_db.js) for the Gaia Dialer app or the recent [Mobile Identity API implementation](https://mxr.mozilla.org/mozilla-central/source/services/mobileid/).

> S: What open source projects would you like to encourage people to participate in, and where can they go to get involved?

> F: Firefox OS of course! No, seriously, I believe Firefox OS gives to software engineers the chance to get involved in an amazing open source community with tons of technical challenges from low-level to front end code. Having the chance to dig into the guts of a web browser and a mobile operative system in such an open environment is quite a privilege. It may seem hard at first to get involved and jump into the process and the code, but there are [already some very nice docs](https://developer.mozilla.org/en-US/Firefox_OS) at the MDN and a lot of nice people willing to help on [IRC (#b2g and #gaia)](https://wiki.mozilla.org/IRC), the mailing lists [(dev-b2g and dev-gaia)](https://lists.mozilla.org/listinfo) or [ask.mozilla.org](https://ask.mozilla.org/questions/).

> S: How can people keep up to date about what you are working on?

> F: I don't have a blog, but I have my [public Github account](https://github.com/ferjm) and my [Twitter account](https://twitter.com/f_jimenez).


In the next article, I interview Brian Warner from the Cloud Services team. Brian is a security expert who shares his thoughts on architecting for security, analyzing threats, "belts and suspenders", and writing code that can be audited.

As a final note, I have had a lot of fun doing these interviews and I would like your input on how to make this series useful to you. If you have suggestions or would like to nominate somebody to be interviewed, please let me know! I even invite you to offer to have yourself interviewed. The Mozilla community has so much to offer. Email me at [stomlinson@mozilla.com](mailto:stomlinson@mozilla.com).
