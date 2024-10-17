---
layout: post
title: Problem Solving Exercises
date: 2024-10-16 12:00:00 +0000
description: Problem Solving Exercises to get your stared in programming. Explore classic problem-solving exercises and riddles to sharpen your programming and critical thinking skills. From the River Crossing Puzzle to logic challenges like the Sibling Riddle and Car Colour Puzzle, these examples help improve planning, deduction, and reasoning. Ideal for both beginners and seasoned puzzle enthusiasts, discover solutions that teach you to think ahead, identify contradictions, and break down problems logically. # Add post description (optional)
img: problem_solving.jpg # Add image post (optional)
tags: [ProblemSolving, LogicPuzzles,CriticalThinking,  ProgrammingChallenges, BrainTeasers] # add tag

---

Here are some problem-solving exercises to help you on your programming journey. These are classic examples nothing fancy, but useful for practice, just like the ones I used when learning to program.

A classic example of a problem-solving exercise is the **"River Crossing Puzzle"**. This puzzle tests logic, planning, and critical thinking. Here's how it works:

### River Crossing Puzzle

### The Problem:
You are on one side of a river with a boat, and you need to transport a **wolf**, a **goat**, and a **cabbage** to the other side of the river. However, there are a few conditions:

1. The boat can only carry you and **one** of the three items (wolf, goat, or cabbage) at a time.
2. You cannot leave the wolf and the goat together unsupervised (the wolf will eat the goat).
3. You cannot leave the goat and the cabbage together unsupervised (the goat will eat the cabbage).

### Objective:
Figure out how to get all three (the wolf, the goat, and the cabbage) across the river without any of them being eaten.

<div id="collapsible-content1" style="display: none;">
  <h3>Solution Process:</h3>
  <p>Here is a step-by-step solution:</p>
  <ol>
    <li><strong>Step 1</strong>: Take the <strong>goat</strong> across the river and leave it on the other side.</li>
    <li><strong>Step 2</strong>: Go back alone to the starting side.</li>
    <li><strong>Step 3</strong>: Take the <strong>wolf</strong> across the river.</li>
    <li><strong>Step 4</strong>: Bring the <strong>goat</strong> back to the starting side.</li>
    <li><strong>Step 5</strong>: Take the <strong>cabbage</strong> across the river.</li>
    <li><strong>Step 6</strong>: Go back alone to the starting side.</li>
    <li><strong>Step 7</strong>: Take the <strong>goat</strong> across the river again.</li>
  </ol>
  <p>At the end of these steps, all three (the wolf, goat, and cabbage) are safely on the other side of the river.</p>

  <h3>Takeaway:</h3>
  <p>This exercise teaches you to think ahead and understand the consequences of each action, emphasizing the importance of careful planning in problem-solving.</p>
</div>
<button id="toggle-button1" onclick="toggleContent('collapsible-content1','toggle-button1')">Show Solution</button>


### The Sibling Riddle

### The Problem:
There are three siblings: **Alex**, **Blake**, and **Charlie**. They are talking about their ages:
- Alex says: "I am not the youngest."
- Blake says: "I am older than Alex."
- Charlie says: "I am not the oldest."

One of them is lying. Can you figure out who is the youngest, the oldest, and who is lying?

<div id="collapsible-content2" style="display: none;">
  <h3>Solution:</h3>
  <ol>
    <li>If Alex were the youngest, then Alex's statement ("I am not the youngest") would be a lie. So, Alex <strong>cannot</strong> be the youngest.</li>
    <li>If Blake's statement ("I am older than Alex") were true, then Alex must be younger than Blake.</li>
    <li>If Charlie were the oldest, then Charlie's statement ("I am not the oldest") would be a lie. So, Charlie <strong>cannot</strong> be the oldest.</li>
  </ol>
  
  <p>Based on these deductions:</p>
  <ul>
    <li>Alex is not the youngest.</li>
    <li>Blake is older than Alex.</li>
    <li>Charlie is not the oldest.</li>
  </ul>

  <p>So, Blake is the oldest, Alex is the middle child, and Charlie is the youngest. <strong>Charlie</strong> is the one lying.</p>

  <p>This riddle involves logical deduction based on conflicting statements.</p>

  <h3>Takeaway:</h3>
  <p>This puzzle emphasizes the value of logical deduction by examining statements for contradictions. It teaches the importance of eliminating impossibilities to reveal the correct answer.</p>
</div>
<button id="toggle-button2" onclick="toggleContent('collapsible-content2','toggle-button2')">Show Solution</button>


### The Missing Dollar Riddle

### The Problem:
Three friends go to a restaurant and order a meal costing $30. They each contribute $10, for a total of $30. The waiter realizes there was a mistake, and the meal only costs $25. The waiter gives $5 back to the friends. 

However, the friends decide to tip the waiter $2 and split the remaining $3 equally among themselves. So, each friend gets $1 back. 

Now, each friend has spent $9 (since they originally gave $10 and got $1 back), and 3 friends spending $9 each equals $27. Plus, the $2 tip given to the waiter totals $29. 

### The Question:
Where is the missing dollar? Shouldn't the total be $30?

<div id="collapsible-dollar-riddle-solution" style="display: none;">
  <h3>Solution:</h3>
  <p>There’s no missing dollar! The confusion arises because of a misinterpretation of the problem. The $27 already includes the $2 tip (so $25 for the meal + $2 tip). You shouldn’t add the tip again; the remaining $3 went back to the friends. This riddle is a good exercise in logical thinking and identifying where errors in reasoning occur.</p>

  <h3>Takeaway:</h3>
  <p>This riddle teaches how easy it is to make mistakes with basic arithmetic when totals and sub-totals are misinterpreted. It highlights the importance of breaking problems down correctly to avoid logical fallacies.</p>
</div>
<button id="toggle-button3" onclick="toggleContent('collapsible-dollar-riddle-solution','toggle-button3')">Show Solution</button>


### Car Colour Puzzle

### The Problem:
Five cars are parked in a line, each with a different colour: **Red, Blue, Green, Yellow, and Black**. Based on the following clues, can you determine the position of the **Yellow car** in the queue?

1. The **Red car** is immediately ahead of the **Blue car**.
2. The **Green car** is at the end of the line.
3. The **Yellow car** is somewhere between the **Red car** and the **Black car**, but it is not next to either of them.
4. The **Blue car** is not next to the **Black car**.

<div id="collapsible-solution-car" style="display: none;">
  <h3>Solution:</h3>
  <p>Let’s work through the clues step by step:</p>
  <ol>
    <li>From clue (2), the <strong>Green car</strong> is in position 5 (the last position).</li>
    <li>From clue (1), the <strong>Red car</strong> is immediately ahead of the <strong>Blue car</strong>. So, the <strong>Red car</strong> must be in position 1, and the <strong>Blue car</strong> must be in position 2.</li>
    <li>From clue (4), the <strong>Blue car</strong> is not next to the <strong>Black car</strong>, so the <strong>Black car</strong> cannot be in position 3.</li>
    <li>From clue (3), the <strong>Yellow car</strong> is somewhere between the <strong>Red car</strong> and the <strong>Black car</strong>. Since the <strong>Red car</strong> is in position 1 and the <strong>Black car</strong> cannot be in position 3, the <strong>Black car</strong> must be in position 4, and the <strong>Yellow car</strong> must be in position 3.</li>
  </ol>

  <p>Thus, the <strong>Yellow car</strong> is in position 3. The final order is:</p>
  <ol>
    <li><strong>Red</strong></li>
    <li><strong>Blue</strong></li>
    <li><strong>Yellow</strong></li>
    <li><strong>Black</strong></li>
    <li><strong>Green</strong></li>
  </ol>

  <p>This puzzle is a good exercise in logic and deduction!</p>

  <h3>Takeaway:</h3>
  <p>This puzzle highlights the need to methodically apply clues to narrow down possibilities. It demonstrates how complex problems can be solved through logical deduction and careful reasoning.</p>
</div>
<button id="toggle-button4" onclick="toggleContent('collapsible-solution-car','toggle-button4')">Show Solution</button>


You can find more problem solving exercises in books and blogs such as:

### References

### Books:
1. [**"The Moscow Puzzles" by Boris A. Kordemsky**](https://www.amazon.co.uk/Boris-Kordemsky-Puzzles-Mathematical-Recreations/dp/B00HTJMZ58/ref=sr_1_1?crid=3L9G58Y8ZYGHT&dib=eyJ2IjoiMSJ9.6xbkzhB93iVBVDOuFgNdpdYftYLFDCBH52mnQxvZ3yQBeaFKP8ne6RTvtpz53W25.PGl_sEcfvh1NG2laonb6NyqoEU8huyDtXK7P_ngQOcA&dib_tag=se&keywords=The+Moscow+Puzzles%E2%80%9D+by+Boris+A.+Kordemsky&nsdOptOutParam=true&qid=1729100821&sprefix=the+moscow+puzzles+by+boris+a.+kordemsky%2Caps%2C79&sr=8-1)  
   This book contains over 350 puzzles, ranging from simple to complex, including logic problems and reasoning challenges like the car colour puzzle or the wolf, goat, and cabbage problem.
   
   
2. [**"Mind-Stretching Puzzles" by Martin Gardner**](https://www.amazon.co.uk/Entertaining-Mathematical-Puzzles-Dover-Recreational/dp/0486252116/ref=sr_1_1?crid=JP960EH7SOJT&dib=eyJ2IjoiMSJ9.zmGMxAyobIj-aH5ahjcZQzSZtDuqJ-pvv_7jS9okh1zLx3bEKQqdlNiYNOB_Rjct9jpTBqQqqFVbnUou6KnM9PqW_nJ3SG99vgYueNEUz1I.f5_RchzPFAm8-FnxN3ZaG3pjfR6H9EeJu_Kl5zlG7J8&dib_tag=se&keywords=Mind-Stretching+Puzzles%22+by+Martin+Gardner&nsdOptOutParam=true&qid=1729101027&sprefix=mind-stretching+puzzles+by+martin+gardner%2Caps%2C60&sr=8-1)  
   Martin Gardner's puzzles focus on logic, reasoning, and mathematical challenges. His puzzles are designed to make you think critically and are similar to the types of exercises you're asking for.

3. [**"Posers, Puzzles and Problems" by Terry Stickels**](https://www.amazon.co.uk/Mind-Bending-Puzzles-Provocative-Posers/dp/0764910264)  
   This book offers a variety of brain teasers and logic puzzles suitable for all levels, including puzzles about sequences, relationships, and positions—perfect for those who enjoy solving problems similar to the car queue puzzle.

### Blogs:
1. **Puzzling Stack Exchange**  
   This is a community-driven blog where users post various types of puzzles, ranging from beginner to advanced, including logic puzzles, riddles, and problem-solving exercises.  
   [Puzzling Stack Exchange](https://puzzling.stackexchange.com)

2. **Brilliant.org**  
   Brilliant is an interactive learning platform with logic puzzles, math problems, and reasoning exercises that will challenge your brain and help you develop critical thinking skills.  
   [Brilliant.org](https://brilliant.org)

3. **Braingle**  
   Braingle is a blog dedicated to brain teasers, riddles, and logic puzzles, with thousands of puzzles that test different problem-solving techniques, perfect for beginners and advanced puzzlers.  
   [Braingle](http://braingle.com) 




>This page was last update at {{ "now" | date: "%Y-%m-%d %H:%M" }} 


