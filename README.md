# Assignement2_kikkuri
## sri Harsha kikkuri.
# My villge <br>
**bodhan** is my **home** town

---

# Directions from Maryville to Bodhan
1. Drive to Kansas Airport
3. Board to chicago Airport.
2. Board to Hyderabad.
     1. Hire a taxi from Airport to Bus Stop.
     2. Travel to Nizamabd.
     5. Hire a taxi to Bodhan from Nizamabad.
* swim suit
* books
* cricket kit

[AboutMe link](AboutMe.md)

---

## Mostly popular Food/Drinks
below table illustrates some drinks and food items which i recommend to try

|Food/Drinks   | Location  | Price($) |
|--------------| --------- | ----- |
| chicken      | bodhan    |  10   |
| Tandoori     | punjab    |  15   |
| burfi        |sikkim     |  7    |
| Pani puri    | hyderbad  |  5    |
| Faluda       | banglore  |  14   |

---

# Pithy Quotes
I have only made this letter longer because I have not had the time to make it shorter.-"Blaise Pascal"<br>
Mathematicians deal with large numbers sometimes, but never in their income.-"Isaac Asimov"

---
# Code Fencing
---
int m, n;
vector<long long> dp_before(n), dp_cur(n);

long long C(int i, int j);

// compute dp_cur[l], ... dp_cur[r] (inclusive)
void compute(int l, int r, int optl, int optr) {
    if (l > r)
        return;

    int mid = (l + r) >> 1;
    pair<long long, int> best = {LLONG_MAX, -1};

    for (int k = optl; k <= min(mid, optr); k++) {
        best = min(best, {(k ? dp_before[k - 1] : 0) + C(k, mid), k});
    }

    dp_cur[mid] = best.first;
    int opt = best.second;

    compute(l, mid - 1, optl, opt);
    compute(mid + 1, r, opt, optr);
}

int solve() {
    for (int i = 0; i < n; i++)
        dp_before[i] = C(0, i);

    for (int i = 1; i < m; i++) {
        compute(0, n - 1, 0, n - 1);
        dp_before = dp_cur;
    }

    return dp_before[n - 1];
}
---
https://cp-algorithms.com/dynamic_programming/divide-and-conquer-dp.html




