---
layout: post
comments: true
title: First Full Project
---

I have been intermittently working through the Web Developer Bootcamp from Colt Steele on Udemy.  I've just completed section 15, and this was a code-along type project of building out some game logic for a color selection game.

I tried to do this a little differently, though.  I did a code-along at the beginning to get the basic framework down.  At that point, every time there was a new piece to add to the project, I paused the video and did it myself first to see if I could do it, then continued.  This turned out some interesting results.

First, in most cases, I implemented in the same logical way, many times even the exact same way.  The interesting part came when there was some refactoring that needed to be done.  Looking at the code that was presented originally, there was a lot of duplicate so I refactored it without knowing that the course was going to do it.  

Additionally, I left out some refactors to loop over a set of buttons to add functionality.  I feel like the use-cases of how many buttons that add a difficulty level would be few and far between.  It also felt like the way it was implemented would be more difficult to maintain the buttons in the future if new levels were to be added.

Here is the example:

{% highlight javascript %}
function setupModeButtons(){
	for(var i = 0; i < modeButtons.length; i++){
		modeButtons[i].addEventListener("click", function(){
			modeButtons[0].classList.remove("selected");
			modeButtons[1].classList.remove("selected");
			this.classList.add("selected");
			this.textContent === "Easy" ? numSquares = 3: numSquares = 6;
			reset();
		});
	}
}
{% endhighlight%}

Here's the way I did it.  I feel like this is something that would be easier to maintain, but I may be wrong.

{% highlight javascript %}
easyButton.addEventListener("click", function() {
  easyButton.classList.add("selected");
  hardButton.classList.remove("selected");
  gameMode = "easy";

  resetGame();
});

hardButton.addEventListener("click", function() {
  hardButton.classList.add("selected");
  easyButton.classList.remove("selected");
  gameMode = "hard";

  resetGame();
});
{% endhighlight%}