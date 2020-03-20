#### Please add your answers to the ***Analysis of  Algorithms*** exercises here.

## Exercise I

a)

The run time for this function is O(n). Although it might appear at first to be n^3 due to the while loop, the interior of the while loop adds n^3 to a every single run. The amount of times that n^2 would need to be added to a to get n^3 is n times, thereby giving this function a run time of O(n).

b)

The runtime for this function is O(n * log2(n)). If the function only had the while loop, the runtime would be log2(n), because you multiply j by 2 every run, making it j * 2^n – and since the input is n, you would reverse the 2^n to become log2(n) to get the runtime. However, the while loop is inside a for loop that loops through n times. Thus, the runtime of the while loop is multiplied by n to get (n)(log2(n)).

c)

The runtime for this function is O(n). The function is a simple recursion that runs itself n number of times for every number between n and 0 – the base case. Every run, the input is reduced by 1 until zero, therefore, the function can run only n number of times (unless given a negative input in which case it would break).

## Exercise II

My solution would run a binary search algorithm on the floors of the building. The code would take the number of floors and create a list of floors, from floor 1 to the maximum. Then the code would separate the floors into two lists and check to see which list f was inside of. Then, the code would take that list and rerun itself, find the new midpoint, cut the building in two, and so on until it reached a length 1 array in which f is located. The function would then return f.
This solution has a runtime of O(log2(n)) since it splits the floors in half every iteration, i.e., it would perform the inverse of 2^n. This is far more efficient than a runtime of O(n) since log2(n) gets increasingly smaller the larger n becomes. To illustrate: an O(n) function would run 100,000 times for an input of 100,000 while an O(log2(n)) function would only run 16.6 times.

Here's the actual solution:

def eggTest(n, f, building=None, runs=0):
    if not building:
      building = [x for x in range(1,n+1)]
    elif f > n:
      return("f not in building")
    elif len(building) <= 1:
      print(f"building size: {n}")
      print(f"number of runs: {runs}")
      return building[0]

    runs += 1

    midpoint = len(building) // 2
    lower = building[:midpoint]
    upper = building[midpoint:]

    if f <= lower[-1]:
      return eggTest(n, f, lower, runs)
    else:
      return eggTest(n, f, upper, runs)


