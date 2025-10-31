# application-
this is the application for my stats presentation
# --- One-sample t-test visualization ---

# Parameters
df <- 15
alpha <- 0.05
t_crit <- qt(1 - alpha, df)   # critical value
t_value <- 2.00               # computed test statistic

# Create range for t values
x <- seq(-4, 4, length.out = 500)
y <- dt(x, df)

# Plot the t-distribution
plot(x, y, type = "l", lwd = 2, col = "black",
     main = "One-Tailed t-Test (df = 15, α = 0.05)",
     ylab = "Density", xlab = "t-value")

# Shade rejection region (right tail)
x_crit <- seq(t_crit, 4, length.out = 100)
y_crit <- dt(x_crit, df)
polygon(c(x_crit, rev(x_crit)), c(y_crit, rep(0, length(y_crit))),
        col = "red", border = NA)

# Mark the critical value
abline(v = t_crit, col = "red", lwd = 2, lty = 2)
text(t_crit, 0.02, paste("t_crit =", round(t_crit, 3)), pos = 4, col = "red")

# Mark the sample t value
abline(v = t_value, col = "blue", lwd = 2)
text(t_value, 0.04, paste("t =", t_value), pos = 4, col = "blue")

# Add legend
legend("topright",
       legend = c("t distribution", "Critical region (α=0.05)", "Observed t = 2.00"),
       col = c("black", "red", "blue"), lwd = 2, lty = c(1, 1, 1))
