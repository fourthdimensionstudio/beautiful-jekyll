---
layout: post
title: Date Differences on Pizza Clicker
image: /img/pizzaclicker/yougot.png
---

Pizza Clicker is an Idle Game targeted for Mobile devices - Someone doesn't really have to do a lot of thinking to find out some flaws in this combination. The first one is that gameplay time on mobile devices tend to be shorter, so how are you going to accumulate resources without spending a lot of time on the game? The second is that keeping the game running on background all the time would kill your smartphone battery.

The solution is simple and not innovative at all, *Adventure Capitalist* already did something like this on Facebook.

## The Solution

The solution is basically giving the player the resources based on real time passage when the app is not running, so the player only open it a few times a day to spend the resources, and it consists of three simple steps:
1. Persisting the date in the game state.
2. Checking how many time passed since last game state persisted.
3. Knowing how many time passed, you just have to multiply it by resources/second the player has.

The first step is really simple, it is all done on the following code:

```
PlayerPrefs.SetString(lastDate, System.DateTime.Now.ToBinary().ToString());
```

Seems pretty dense, but it isn't really, `lastDate` is just a string variable I'm using to define the key used for setting the PlayerPrefs. The second part is a bit more cryptical: `System.DateTime.Now.ToBinary().ToString()` but it just means I'm saving, as a string, the current time in a binary format.

The second step is a little bit more unintuitive, here it goes:

```
System.DateTime currentDate = System.DateTime.Now;
long tempDate = System.Convert.ToInt64(t_saveState.lastSavedDate);
System.DateTime oldDate = System.DateTime.FromBinary(tempDate);
System.TimeSpan difference = currentDate.Subtract(oldDate);
```

As you can see, the variable `tempDate` is created by converting to a `long` the DateTime value saved on the PlayerPrefs (the whole save state is persisted on this t_saveState variable). And then this value is used to create a DateTime variable. All of this could probably be done in the same line, giving the following result: `System.DateTime oldDate = System.DateTime.FromBinary(System.Convert.ToInt64(t_saveState.lastSavedDate));`

This conversion was the tricky part for me to figure out and probably is going to be for others in the future. But it's not difficult at all, just need to use some System functionalities.

At the last line, the difference between the dates are calculated and then we have our difference so we can give the resources to the player!

And finally, to see the difference in seconds, this simple Debug.Log will do: `Debug.Log("difference: " + difference.TotalSeconds);` - As you can observe, the difference is a TimeSpan, not a DateTime, the TimeSpan has a whole lot of methods and attributes to help us measure the time passed by.

And, visually, we can do this:

![Pizza Clicker](/devlog/img/pizzaclicker/yougot.png)

This is a simple post but it is a very useful implementation on a nice design decision for idle games!

Have a nice day and until next post!

Don't forget to follow Fourth Dimension on [Twitter](https://twitter.com/studio_fourth)!
