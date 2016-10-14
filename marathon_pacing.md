
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
