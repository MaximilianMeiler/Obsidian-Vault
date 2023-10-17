https://onlinejudge.org/index.php?option=onlinejudge&Itemid=8&page=show_problem&problem=3644

Given a set of events happening every x ticks, output the first y events that occur in order

- Add a tuple of (time, event number, base time) to a priority queue for each input
- When an event is run from the top of the queue, add its base time to the execution time and return it into the queue
