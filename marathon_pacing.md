
Pacing grid:

| Miles	| 7:00 | 7:30 | 8:00 | 8:30 | 9:00 |
|-------|------|------|------|------|------|
| 3.1	  | 0:22 | 0:23 | 0:25 | 0:26 | 0:28 |
| 5		  | 0:35 | 0:38 | 0:40 | 0:42 | 0:45 |
| 6		  | 0:42 | 0:45 | 0:48 | 0:51 | 0:54 |
| 6.2	  | 0:43 | 0:46 | 0:50 | 0:53 | 0:56 |
| 7		  | 0:49 | 0:52 | 0:56 | 0:60 | 1:03 |
| 8		  | 0:56 | 1:00 | 1:04 | 1:08 | 1:12 |
| 13.1  | 1:32 | 1:38 | 1:45 | 1:51 | 1:58 |
| 26.2  | 3:03 | 3:16 | 3:30 | 3:43 | 3:56 |

```{r}
## setup
dists <- c(3.1,5,6,6.2,7,8,13.1,26.2)
times <- seq(7, 9, by=0.5)
A <- as.matrix(dists)
B <- t(as.matrix(times))

## calc paces
mins <- A %*% B
hrs <- mins / 60
p1 <- floor(mins/60)
p2 <- as.character(round((mins / 60 - floor(mins/60))*60,0))
p2[nchar(p2)==1] <- paste0("0", p2[nchar(p2)==1])

## calc pace grid
pace <- as.data.frame(matrix(paste0(p1, ":", p2), nrow=length(dists)))
names(pace) <- paste0(floor(times), ":", (times-floor(times)) * 6, "0")
rownames(pace) <- dist 
pace
```
