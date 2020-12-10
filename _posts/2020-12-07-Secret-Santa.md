---
published: true
---
## Secret Santa Problem

Secret Santa is a Western Christmas tradition in which members of a group or a community are randomly assigned a person to whom they give a gift. The identity of the gift giver is to remain a secret and should not be revealed, that's why it's called secret Santa!

### Analog Edition

People would write names on small pieces of paper (like sticky notes) and put them in a Santa hat. 
Then every participating member will pick one of the notes to find out whom they should be giving a gift  this year.

![Screen Shot 2020-12-07 at 8.30.20 PM.png]({{site.baseurl}}/images/2020-12-07-Secret-Santa/Screen Shot 2020-12-07 at 8.30.20 PM.png)

**Even though we shuffled the names in the hat, there's a chance that we'll pick our name**.
So let's say that Barbara picks herself, what should she do? Usually, people would put back the note with their name and try again. But now we know that Barbara is not picked by anyone.
This might be okay if we just started the game, but what if there were only 2 notes left? For example, if Jennifer had to put her name back, and then Karen picked the last name - we know she picked Jennifer.
It's not a randomized anonymous assignment anymore…

### How do we solve this problem?
Well… we can restart the entire game every time somebody picks their own name. As you probably already figured out, it might take quite some time.

**Let's figure out how we can solve this small inefficiency…**

Instead of names, we can prepare cards with indexes, to look like this: 1-> 2, 2-> 3, 3-> 1, where the first number would be the number issued to the person who picked that card, and the second number is the person who will be receiving their gift.         

![Screen Shot 2020-12-07 at 8.47.38 PM.png]({{site.baseurl}}/images/2020-12-07-Secret-Santa/Screen Shot 2020-12-07 at 8.47.38 PM.png)

Then we shuffle the cards in the hat and let each participant pick a card.

![Screen Shot 2020-12-07 at 8.55.44 PM.png]({{site.baseurl}}/images/2020-12-07-Secret-Santa/Screen Shot 2020-12-07 at 8.55.44 PM.png)

At this moment we might ask everyone to fill the index with their names (based on the first number and not show the second number to anybody):
1 - Barbara
2 - Lisa
3 - William
4 - Richard
5 - Thomas
6 - Karen
7 - Jennifer

Now, everybody knows who they will be giving a gift to this year:
- William -> Richard
- Barbara -> Lisa
- Jennifer -> Barbara
- Thomas -> Karen
- Lisa -> William
- Karen -> Jennifer
- Richard -> Thomas

### Digital Edition

Now, in the era of COVID, we might want to digitalize this game, here's where I'd to take a look into [Sattolo's shuffling algorithm](https://en.wikipedia.org/wiki/Fisher%E2%80%93Yates_shuffle#Sattolo%27s_algorithm).

It's just like the regular Collections.shuffle() but this way it guarantees that every member will have new position in the shuffled list.

```java
private <T> List<T> shuffle(List<T> list) {
  final ArrayList<T> shufflingList = new ArrayList<>(list);
  for (int i = 0, secondToLast = shufflingList.size() - 1; i < secondToLast; i++) {
    final int shift = i + 1;
    final int swapCandidate = random.nextInt(shufflingList.size() - shift) + shift;
    Collections.swap(shufflingList, i, swapCandidate);
  }
  return shufflingList;
}
```
and then we can use it to prepare our list for Secret Santa
```java
public Map<Person, Person> matchMembers(List<Person> familyMembers) {
  final List<Person> receivers = shuffle(familyMembers);
  final int familySize = familyMembers.size();
  final Map<Person, Person> secretSanta = new HashMap<>(familySize);
  for (int i = 0; i < familySize; i++) {
    secretSanta.put(familyMembers.get(i), receivers.get(i));
  }
  return secretSanta;
}
```

Result:
![Screen Shot 2020-12-07 at 9.28.22 PM.png]({{site.baseurl}}/images/2020-12-07-Secret-Santa/Screen Shot 2020-12-07 at 9.28.22 PM.png)
