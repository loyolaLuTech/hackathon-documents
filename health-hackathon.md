##Health Hackathon Judging Guidelines

In order to encourage every team to do EVERY aspect of a project, not just code, LuTech has devised the following system:

###The Skinny:

It is in the best interest of a project to be significantly above average in a category. This judging system works such that only points that count are in categories where a group scored above average as compared to the other groups.

If everyone did poorly in one category and one group did well <-- this is worth a lot

If most people did well in a category <-- this is worth less

####Points:

Points are awarded based on the following categories, each judge gets a vote and the scores are averaged:

* _Relevance:_ 0-4 pts
	* How well does the project relate to health?

* _Idea:_ 0-10 pts
	* Will this project do any good?  Is it a good idea?

* _Theoretical design:_ 0-8 pts
	* Is the idea well implemented?

* _Technical Impressiveness:_ 0-14 pts
	* Was the problem solved efficiently/elegantly?
	* Was the problem hard to implement/solve?

* _Usefulness/Practicality:_ 0-10 pts
	* Can the product be actualized?
	* Would this product, once complete, be useful to it's intended audience?

###Extra Points:

These points are not averaged, just awarded to groups at the end of the judging algorithm:

* _JudgesChoice_: .5 pts
  * Each judge gets .5 points to assign to their favorite project.

* _EboardsChoice_: .2 pts
  * Each eboard member gets .2 points to assign to their favorite project

* _ThePrettyPoint_: .5 pts
  * .5 points are assigned to the prettiest presentation by the eboard.

###Algorithm:

Project judgement is based on categories. The average scores for each category is taken, and groups receive points based on how much above the average they are.

So, for example, if everyone got points in the following way:

```
GroupA 5   4   0
GroupB 5   4   0
GroupC 5   4   0
GroupD 5   3   1

Averag 5  3.75 .25

AwardA 0  .25  0
AwardB 0  .25  0
AwardC 0  .25  0
AwardD 0   0  .75   
```

Group C would win with .75 points. A,B and C would have .25. Regardless of the fact that they had the same point count.

This is done to encourage no group ignore lower value categories for higher value ones.

To illustrate ONLY:

```java
Double[] Group1 = new Double[] {0,0,0,0,0};
Double[] Group2 = new Double[] {0,0,0,0,0};
Double[] CategoryAverages = new Double[]{0,0,0,0,0};
Double group1score = 0;
Double group2score = 0;
Double[] groupScores = new Double[]{group1score,group2score};

Double[][] groups = new Double[][]{Group1, Group2};

for (int i = 0; i < groups.size; i++) {
  Double [] curr = groups[i];
  for (int c = 0; c < curr.size; c++){
    curr[c] = ReadCategoryScore(); //Get averaged scores of judges for the group for the category
    CategoryAverages[c] += curr[c];
  }
}
for (int i = 0; i < CategoryAverages.size; i++){
  CategoryAverages[i] /= groups.size;
}
for (int i = 0; i < groups.size; i++) {
  Double [] curr = groups[i];
  for (int c = 0; c < curr.size; c++){
    curr[c] = curr[c]-CategoryAverages[c];
    if (curr[c]<0) curr[c]=0;
    groupScores[i]+=curr[c];
  }
}

//Add bonuses here
```
