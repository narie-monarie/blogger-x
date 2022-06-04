# Next Round

"Contestant who earns a score equal to or greater than the _k_-th place finisher's score will advance to the next round, as long as the contestant earns a positive score..." — an excerpt from contest rules.

A total of _n_ participants took part in the contest $$(n_ ≥ k_)$$, and you already know their scores. Calculate how many participants will advance to the next round.

Input

The first line of the input contains two integers _n_ and _k_ $$(1 ≤ k ≤ n ≤ 50)$$ separated by a single space.

The second line contains _n_ space-separated integers $$a_1, a_2, ..., a_n$$ $$(0 ≤ a_i ≤ 100)$$, where _a__i_ is the score earned by the participant who got the $$i_-th$$ place. The given sequence is non-increasing (that is, for all _i_ from 1 to _n_ - 1 the following condition is fulfilled: $$(a_i ≥ a_i + _1).$$

Output

Output the number of participants who advance to the next round.

=== Examples
||| Sample 1
```
input
8 5  
10 9 8 7 7 7 5 5  

output
6   
```

||| Sample 2 
```
input
4 2  
0 0 0 0  

output
0  

```
||| 

**Note**

In the first example the participant on the 5th place earned 7 points. As the participant on the 6th place also earned 7 points, there are 6 advancers.

In the second example nobody got a positive score.
=== Solution In Golang

```go
package main

import "fmt"

func main() {
	//n is the number of questions
	//m is the pass mark
	var n, m int
	fmt.Scanln(&n, &m)
	a := make([]int, n)

	for i := 0; i < n; i++ {
		fmt.Scanf("%d", &a[i])
	}

	count := 0
	for i := 0; i < n; i++ {
		if a[i] >= a[m-1] && a[i] != 0 {
			count++
		}
	}

	fmt.Println(count)
}
```
===