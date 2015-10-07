---
layout: post
title: "Cleaning Your Code Using 'this,' With 'attr()'"
date: 2015-09-17 18:13:39 -0500
comments: true
categories: 
---

My first post-class blog is on the gallery page I made for my portfolio website, which was one of our end-of-class final projects. We wanted a page to show the projects we'd worked on in class, and demonstrate the things we'd learned so far. As a total newbie in programming, I was very proud with what I came up with for my gallery page. Start simple: show a small picture of each project, have a description for each image, and make each image link to the actual project. Use a 'ul' and have each 'li' contain an 'a' with an 'img' inside the 'a'. Great, but beginner or not, I couldn't leave the page this simple! We'd learned some Jquery, so I figured out how to have css hide each description and use Jquery to have each description slide onto the page when it's corresponding image was hovered over. While I was at it, I used the css pseudo-class ':hover' with the 'img' selector, `img:hover`, and `{transform: scale(1.5), transition: .75s}` to have each image get larger in view while it was being hovered over, and while the description was sliding in from the bottom.

<p style='margin:0'>
Often in programming, the valuable lessons are not in learning how to get the computer to do something. That's just a matter of memorizing commands and letting the magic work: copy-and-paste magic, if you will. It's just 'mouseenter','mouseleave', 'show', and 'animate': 
<pre style='margin:0 0 0 10%;padding:0 0 0 5%; color:purple; background: #B2B2B2; font-weight: bold;'>
$('#id of image').on({mouseenter: function() { 
  $('#id of description').show().animate({'right': '10%'}, 1500);
  },
  mouseleave: function() {
  $('#id of description').animate({'right': '-100%'});
  }
});
</pre>
</p>
<p style='margin:default'>
One valuable lesson, maybe the first for a beginner, is using your knowledge of programming to clean your code. Clean code does not repeat itself, and we use the acronym DRY, for Don't Repeat Yourself. Can you imagine how horrible it would be to read a book by an author who constantly repeats himself over and over? Take the above code, for example. I have to repeat that entire code for every single image and description in my gallery. That's just bad programming. There should be a way to write the code so that it performs this function for every image the user hovers over, without having to re-write it each time. 
</p>
<p style='margin:default'>
We start with the first line, and change '#id of image' to it's parent, 'ul img.' <code>$('ul img').on({mouseenter: function() {</code> That should activate the mouseenter function for every li image hovered over in the ul. Jquery's "$('ul img')" takes all the image tags in the ul and puts them in an array. It is the same as JavaScripts's "document.querySelectorAll('ul img')". 
</p>
<p style='margin:0'>
For the next step, usually, you would think of if/else conditionals in such situations, since we often use conditionals when looping over arrays: if the mouse hovers over $('ul img')[0], then show the description that matches, if the mouse hovers over $('ul img')[1], then show the matching description. What would your if-conditional statement be? If ul img == ul img[0]?? That doesn't work. The array will never be equal to an element inside of it. Remember, in JavaScript, an array is an object. "When a function is called as a method of an object, its 'this' is set to the object the method is called on." <a style='color:purple'>https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/this</a>. The first part of this statement - "When a function is called as a method of an object," - is exactly what's happening when you code "$('ul img').on()". "$('ul img')" is a JavaScript object. (You need to understand the DOM API to understand why html tags are JavaScript objects.) If you recall, methods are object properties whose value is a function. ".on()" is a method of the "$('ul img')" object. When you are using the mouseenter function on several li items, 'this' will tell the program to focus only on the li being hovered over by the mouse. Now my code can look like:
<pre style='margin:0 0 0 10%;padding:0 0 0 5%; color:purple; background: #B2B2B2; font-weight: bold;'>
$('#id-of-ul img').on({mouseenter: function() {
    if (this == $('#projects img')[0])
        $('#id of description').show().animate({'right': '10%'}, 1500);
    if (this == $('#projects img')[1])
        $('#id of description').show().animate({'right': '10%'}, 1500);
    if (this == $('#projects img')[2])
        $('#id of description').show().animate({'right': '10%'}, 1500);
    }
});
</pre>
</p>
<p style='margin:0'>
 The obvious problem is that writing a conditional for every situation doesn't help us shrink our code anymore than if we just re-wrote the function for each item, as we did in the beginning. If I'm not re-writing code for each li item, and I'm not using if/else conditionals for the same reason (DRY), then how do I code which description div to show when the mouse hovers over the image? This is a perfect example problem for a beginner on proper use of html attributes for coding purposes, taking their programming skill out of the copy-and-paste magic into their first bit of original programming. The id attribute in html 5 was essentially created for Javascript, and was meant to be retrieved by Javascript for the very purpose of selecting elements. The class attribute should be used for css, but certainly can be used in Javascript if necessary. You'll notice the id atttributes of the image and it's corresponding description are almost exactly the same, obviously, because the one is for the other. Essentially, the id for the description that you need to show is already contained in the id attribute for the image. The difference can be as small as a dash, '-'. So as long as we retrieve our id attribute value from the li and store it in a variable, simple string concatenation gets us our id for the description by adding a '-d' to the variable. Now we have a variable that changes depending on what is being hovered over, and we can write our code like this:
 <pre style='margin:0 0 0 10%;padding:0 0 0 5%; color:purple; background: #B2B2B2; font-weight: bold;'>
$('#id-of-ul img').on({mouseenter: function() { 
    var description = $(this).attr('id') + '-d';
    $('#' + description).show().animate({'right': '10%'}, 1500);
    },
    mouseleave: function() {
    var description = $(this).attr('id') + '-d';
    $('#' + description).animate({'right': '-100%'});
    }
});
</pre>
Finally, we are DRY! You'll notice there is one last line of duplication, "var description: = $(this).attr('id') + '-d'." This is still DRY code even with that duplication, because there is no way around it. Unfortunately, because the value of the variable "description" is "$(this)", you cannot save the variable in the global environment. If you try, the value of the variable simply comes back undefined. I do hate having to write that line twice, but it is succinct nonetheless. 
</p>
<p style='margin:default'>
"This", coupled with the "attr()" method, prevents us from having to specify each li tag, either by writing a mouseenter function for each one, "$('#id of image')", or using if/else conditionals with "$('ul img')[0]", "$('ul img')[1]", and "$('ul img')[2]." They make our code DRY. They also allow us to write a dynamically altered code, i.e. we dont' have to add to the code everytime we change or add to our list of images and descriptions. 
</p>
<p style='margin:0'>
p.s. here is the code using pure JavaScript (without animation):
<pre style='margin:0 0 0 10%;padding:0 0 0 5%; color:purple; background: #B2B2B2; font-weight: bold;'>
var projects = document.querySelectorAll('#projects img');
    for (var i=0; i < projects.length; i++) {
        projects[i].addEventListener('mouseenter', function() {
        var description = this.id + '-d';
        document.getElementById(description).style.display = 'block';
        })
        projects[i].addEventListener('mouseleave', function() {
        var description = this.id + '-d';
        document.getElementById(description).style.display = 'none';
        })
    }
</pre>
</p>