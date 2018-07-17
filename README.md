 Shiny application that uses simulated annealing to solve the famous traveling salesman problem.

# How does the simulated annealing process work?

We start by picking an arbitrary initial tour from the set of all valid tours. From that initial tour we ¡°move around¡± and check random neighboring tours to see how good they are. There are so many valid tours¡ª(47! / 2), to be exact¡ªthat we won¡¯t be able to test every possible solution. But a well-designed annealing process eventually reaches a solution that, if it is not the global optimum, is at least good enough. Here¡¯s a step-by-step guide:

1. Start with a random tour through the selected cities. Note that it¡¯s probably a very inefficient tour!
2. Pick a new candidate tour at random from all neighbors of the existing tour. Via Professor Joe Chang, one way to pick a neighboring tour ¡°is to choose two cities on the tour randomly, and then reverse the portion of the tour that lies between them.¡± This candidate tour might be better or worse compared to the existing tour, i.e. shorter or longer.
3. If the candidate tour is better than the existing tour, accept it as the new tour.
4. If the candidate tour is worse than the existing tour, still maybe accept it, according to some probability. The probability of accepting an inferior tour is a function of how much longer the candidate is compared to the current tour, and the temperature of the annealing process. A higher temperature makes you more likely to accept an inferior tour.
5. Go back to step 2 and repeat many times, lowering the temperature a bit at each iteration, until you get to a low temperature and arrive at your (hopefully global, possibly local) minimum. If you¡¯re not sufficiently satisfied with the result, try the process again, perhaps with a different temperature cooling schedule.

The key to the simulated annealing method is in step 4: even if we¡¯re considering a tour that is worse than the tour we already have, we still sometimes accept the worse tour temporarily, because it might be the stepping stone that gets us out of a local minimum and ultimately closer to the global minimum. The temperature is usually pretty high at the beginning of the annealing process, so that initially we¡¯ll accept more tours, even the bad ones. Over time, though, we lower the temperature until we¡¯re only accepting new tours that improve upon our solution.
