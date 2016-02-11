##Health Hackathon Judging Guidelines

In order to encourage every team to do EVERY aspect of a project, not just code, LuTech has devised the following system:

####Points:

Points are awarded based on the following categories, each judge gets a vote and the scores are averaged:

* _Relevance:_ 0|2 pts
	* 0 - No relation to sustainability
	* 2 - Connects to Chicago sustainability in some way
* _Idea:_ 0-5 pts
	* Will this product do any good?  Is it a good idea?
	* Based on judges averaged votes.
* _Design:_ 0|1 pt + 0-4 pts
	* Visual design
		* 0|1 point. Is it in papyrus?
	* Theoretical design
		* Is the idea well implemented. It works well within its context. Its... "well designed"
		* 0-4 pts based on judges averaged votes.
* _Technical Impressiveness:_ 0-7 pts
	* Curved category. Judges scores averaged.
	* Was the problem solved efficiently/elegantly.
	* Was the problem hard to implement/solve.
* _Usefulness/Practicality:_ 0-5 pts
	* Would this product, in completeness, be useful to it's intended audience?

###Extra Points:

These points are not averaged, just awarded to groups at the end of the judging algortihm:

* _JudgesChoice_: .2 pts
  * Each judge gets .2 points to assign to their favourite project.
* _EboardsChoice_: .1 pts
  * Each eboard member gets .1 pts to assign to their favourite project
* _ThePrettyPoint_: .2 pts
  * By polling. .2 points are assigned to the prettiest presentation by the eboard.

###Algorithm:

The following is not code that is gonna run. Its just meant to illustrate how points are accumulated based on above average points only. Which means each group is granted category points ONLY that they received above the average amount. Thus if everyone ignores a category except for one team, that team will receive a large amount of points for doing it.

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
