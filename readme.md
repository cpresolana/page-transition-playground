the first thing to make barba work is to add                 data-barba="wrapper"
to the body element

after that we can put things in our main element
data-barba="container" 
and then every page must have his unique namespace like
data-barba-namespace="index"

!Important: Barba is not an animation library, we will also use gsap to handle the animations

in the js we initialize barba with

barba.init({
	sync: true,
	transitions: [
		{
			async leave() {
				const done = this.async();
				pageTransition();
				fadeOutContent();
				await delay(1200);
				done();
			},
			async enter() {
				fadeInContent();
			},
			async once() {
				fadeInContent();
			},
		},
	],
});

about sync mode:

sync mod is disabled by default

sync: false will play the leave transition first, then play the enter transition (two step transition)

sync: true will play the leave and the enter transition at the same time (crossfade transition)
