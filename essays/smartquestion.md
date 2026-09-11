---
layout: essay
type: essay
title: "Be Smarter, Not Harder"
# All dates must be YYYY-MM-DD format!
date: 2026-09-10
published: true
labels:
  - Questions
  - Answers
  - StackOverflow
---

<img width="300px" class="rounded float-start pe-4" src="../img/smart-questions/rtfm.png">

## Is there such thing as a stupid question?

Contrary to what you might have been told, there are  actually stupid questions and also unhelpful answers.The desire to learn is not the stupid part, but the inability to search for an answer that is readily available before taking the easy way out is. Here’s what we can do to be smarter about the way we ask questions instead of making things harder for other people and getting unhelpful answers in return.

## Where should I ask my questions?

When you have a problem, you would be inclined to ask for help but where would you ask this question if the people immediately near you don’t have an answer? There are several forums, stack exchanges, pages, social media groups, and more that fill all kinds of niches from programming, painting, gaming, and anything else that might have some dedicated people in the community. Within the context of programming, an easy one that comes to mind is Stack Overflow, a place where there are many questions for software development and programming as well as answers to these problems.

## What exactly is a smart question?

I would say that a smart question is one that clearly outlines the problem and any relevant supporting information, is asked in the correct place, is formatted correctly, provides previous attempts to solve the problem, is not a question that could have been answered in a 5 second Google search, and provides an update after the problem was solved and what worked to solve it.

Eric Raymond outlines this in their essay, “How to ask questions the smart way”, the main steps are as follows:

```
Choose your forum carefully
Use meaningful, specific subject headers
Make it easy to reply
Write in clear, grammatical, correctly-spelled language
Send questions in accessible, standard formats
Be precise and informative about your problem
Volume is not precision
Don't rush to claim that you have found a bug
Grovelling is not a substitute for doing your homework
Describe the problem's symptoms, not your guesses
Describe your problem's symptoms in chronological order
Describe the goal, not the step
Don't ask people to reply by private e-mail
Be explicit about your question
When asking about code
Don't post homework questions
Prune pointless queries
Don't flag your question as “Urgent”, even if it is for you
Courtesy never hurts, and sometimes helps
Follow up with a brief note on the solution
```
But the most important thing to do before formulating the smart question is to look up your question in your search browser, forum, or even LLM of choice which may outright solve your problem before you even have to ask. Additionally, the question should only be asked to fix a specific problem and you should not expect other people to write or debug your entire program for you.

## Example of a smart question: 
https://stackoverflow.com/questions/11227809/why-is-conditional-processing-of-a-sorted-array-faster-than-of-an-unsorted-array


```
Q: Why is conditional processing of a sorted array faster than of an unsorted array?

In this C++ code, sorting the data (before the timed region) makes the primary loop ~6x faster:

#include <algorithm>
#include <ctime>
#include <iostream>

int main()
{
    // Generate data
    const unsigned arraySize = 32768;
    int data[arraySize];

    for (unsigned c = 0; c < arraySize; ++c)
        data[c] = std::rand() % 256;

    // !!! With this, the next loop runs faster.
    std::sort(data, data + arraySize);

    // Test
    clock_t start = clock();
    long long sum = 0;
    for (unsigned i = 0; i < 100000; ++i)
    {
        for (unsigned c = 0; c < arraySize; ++c)
        {   // Primary loop.
            if (data[c] >= 128)
                sum += data[c];
        }
    }

    double elapsedTime = static_cast<double>(clock()-start) / CLOCKS_PER_SEC;

    std::cout << elapsedTime << '\n';
    std::cout << "sum = " << sum << '\n';
}
Without std::sort(data, data + arraySize);, the code runs in 11.54 seconds.
With the sorted data, the code runs in 1.93 seconds.
(Sorting itself takes more time than this one pass over the array, so it's not actually worth doing if we needed to calculate this for an unknown array.)

Initially, I thought this might be just a language or compiler anomaly, so I tried Java:

import java.util.Arrays;
import java.util.Random;

public class Main
{
    public static void main(String[] args)
    {
        // Generate data
        int arraySize = 32768;
        int data[] = new int[arraySize];

        Random rnd = new Random(0);
        for (int c = 0; c < arraySize; ++c)
            data[c] = rnd.nextInt() % 256;

        // !!! With this, the next loop runs faster
        Arrays.sort(data);

        // Test
        long start = System.nanoTime();
        long sum = 0;
        for (int i = 0; i < 100000; ++i)
        {
            for (int c = 0; c < arraySize; ++c)
            {   // Primary loop.
                if (data[c] >= 128)
                    sum += data[c];
            }
        }

        System.out.println((System.nanoTime() - start) / 1000000000.0);
        System.out.println("sum = " + sum);
    }
}
With a similar but less extreme result.

My first thought was that sorting brings the data into the cache, but that's silly because the array was just generated.

What is going on?
Why is processing a sorted array faster than processing an unsorted array?
The code is summing up some independent terms, so the order should not matter.

```

In their observance of a C++ program and nearly identical Java program they created to test out the difference between conditional processing of a sorted vs unsorted array, they noted down time differences, and asked about what was happening and why it was the case.

This question is more asking about the way something works rather than a simple explanation of an operator or syntax, they show that they have experimented with the scenario and observed the differences, and the question is clear in the heading. 

The answer given to this question is also quite frankly, extremely good and well formatted with visualizations, analogies, a look into the inner workings of the system, why the scenario happens, and much more. However it is a bit too in depth to be in this section so I would recommend you to check it for yourself.


## Example of a not so smart question: 
https://stackoverflow.com/questions/37913482/swift-static-let-and-meaning

```
Q: Swift - static let and "<<" meaning [closed]
I have the following code

struct Physics {
    static let smallCoin : UInt32 = 0x1 << 1
    static let smallCoin2 : UInt32 = 0x1 << 2
    static let ground : UInt32 = 0x1 << 3
}
I would like to know the meaning of

static let
UInt32 = 0x1 << 3

```

The things this question asker does well is provide the programming language the problem is about, the functions that they want to know about, the sample code is formatted properly, and they extract the part that they specifically want explained. 

The problem is that a Google search of their header provides the answer for them, especially since the documentation of Swift is online and there exist several online resources. 

The bitwise shift is not unique to Swift and there exists another Stack Overflow question 5 years before this one that asks about the “<<” operator like the above question. There is also a question on Stack Overflow asked 6 months before that asks, “What is the use of "static" keyword if "let" keyword used to define constants/immutables in swift?” which the answers below would have answered the question. 

Despite this, they were still able to receive 2, separate fairly good answers that solved their problem even though a whole lot of time could have been saved even though the asker never came back to leave a note or mark a solution to their answer. However, things won’t always turn out so well as asking obvious questions can earn the ire or sarcastic responses that aren’t helpful.


## Conclusion

The importance of smart questions is that the problem and tools used for the problem are outlined clearly enough for people to provide a solution that matched what the asker has, whoever asks the questions shows that they have attempted their own solutions and that the problem is not a common question that does not need to be asked on a forum, and that they demonstrate basic courtesy and formatting know how. Doing so makes their question easily understandable such that a solution can be found much more easily without guesswork, and ensures that the asker respects the people who see their question and this respect is reciprocated so that everyone is happy when the problem is solved.
