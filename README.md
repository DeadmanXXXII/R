# R
Here is an extensive list of R CLI commands, techniques, and advanced methods for working with R in various environments.

### **Basic R CLI Commands**

#### **1. Basic Operations**

- **Start R:**
  ```sh
  R
  ```

- **Execute R script:**
  ```sh
  Rscript script.R
  ```

- **Install package:**
  ```R
  install.packages("package_name")
  ```

- **Load package:**
  ```R
  library(package_name)
  ```

- **Get help for a function:**
  ```R
  ?function_name
  ```

- **Quit R:**
  ```R
  q()
  ```

#### **2. Working with Data**

- **Read CSV file:**
  ```R
  data <- read.csv("file.csv")
  ```

- **Write CSV file:**
  ```R
  write.csv(data, "file.csv")
  ```

- **Read Excel file:**
  ```R
  install.packages("readxl")
  library(readxl)
  data <- read_excel("file.xlsx")
  ```

- **Read data from URL:**
  ```R
  data <- read.csv("http://example.com/file.csv")
  ```

#### **3. Data Manipulation**

- **View first few rows of data:**
  ```R
  head(data)
  ```

- **View structure of data:**
  ```R
  str(data)
  ```

- **Filter data:**
  ```R
  subset_data <- subset(data, column_name == "value")
  ```

- **Select columns:**
  ```R
  selected_data <- data[, c("column1", "column2")]
  ```

- **Sort data:**
  ```R
  sorted_data <- data[order(data$column_name),]
  ```

- **Merge datasets:**
  ```R
  merged_data <- merge(data1, data2, by = "common_column")
  ```

#### **4. Data Visualization**

- **Plot data:**
  ```R
  plot(data$column1, data$column2)
  ```

- **Histogram:**
  ```R
  hist(data$column_name)
  ```

- **Boxplot:**
  ```R
  boxplot(data$column_name)
  ```

- **Barplot:**
  ```R
  barplot(table(data$column_name))
  ```

- **Advanced plotting with ggplot2:**
  ```R
  install.packages("ggplot2")
  library(ggplot2)
  ggplot(data, aes(x = column1, y = column2)) + geom_point()
  ```

#### **5. Statistical Analysis**

- **Summary statistics:**
  ```R
  summary(data)
  ```

- **Correlation:**
  ```R
  cor(data$column1, data$column2)
  ```

- **Linear regression:**
  ```R
  model <- lm(column1 ~ column2, data = data)
  summary(model)
  ```

- **ANOVA:**
  ```R
  aov_result <- aov(column1 ~ factor_column, data = data)
  summary(aov_result)
  ```

- **t-test:**
  ```R
  t.test(data$column1, data$column2)
  ```

#### **6. Advanced Data Manipulation with dplyr**

- **Install dplyr:**
  ```R
  install.packages("dplyr")
  library(dplyr)
  ```

- **Select columns:**
  ```R
  selected_data <- select(data, column1, column2)
  ```

- **Filter rows:**
  ```R
  filtered_data <- filter(data, column_name == "value")
  ```

- **Arrange rows:**
  ```R
  arranged_data <- arrange(data, column_name)
  ```

- **Mutate (create new columns):**
  ```R
  mutated_data <- mutate(data, new_column = column1 + column2)
  ```

- **Summarize data:**
  ```R
  summary_data <- summarize(data, mean_value = mean(column_name))
  ```

- **Group by and summarize:**
  ```R
  grouped_data <- data %>% group_by(group_column) %>% summarize(mean_value = mean(column_name))
  ```

#### **7. Data Visualization with ggplot2**

- **Scatter plot:**
  ```R
  ggplot(data, aes(x = column1, y = column2)) + geom_point()
  ```

- **Line plot:**
  ```R
  ggplot(data, aes(x = column1, y = column2)) + geom_line()
  ```

- **Bar plot:**
  ```R
  ggplot(data, aes(x = factor_column, y = column_name)) + geom_bar(stat = "identity")
  ```

- **Histogram:**
  ```R
  ggplot(data, aes(x = column_name)) + geom_histogram(binwidth = 10)
  ```

- **Boxplot:**
  ```R
  ggplot(data, aes(x = factor_column, y = column_name)) + geom_boxplot()
  ```

- **Facet wrap:**
  ```R
  ggplot(data, aes(x = column1, y = column2)) + geom_point() + facet_wrap(~ factor_column)
  ```

#### **8. Time Series Analysis**

- **Install and load time series package:**
  ```R
  install.packages("forecast")
  library(forecast)
  ```

- **Create time series object:**
  ```R
  ts_data <- ts(data$column_name, start = c(2020, 1), frequency = 12)
  ```

- **Plot time series:**
  ```R
  plot(ts_data)
  ```

- **Decompose time series:**
  ```R
  decomposed <- decompose(ts_data)
  plot(decomposed)
  ```

- **Forecasting:**
  ```R
  fit <- auto.arima(ts_data)
  forecast_data <- forecast(fit, h = 12)
  plot(forecast_data)
  ```

#### **9. R Markdown and Reporting**

- **Install R Markdown:**
  ```R
  install.packages("rmarkdown")
  ```

- **Create R Markdown document:**
  ```sh
  rmarkdown::draft("report.Rmd", template = "html_document", package = "rmarkdown")
  ```

- **Render R Markdown to HTML:**
  ```R
  rmarkdown::render("report.Rmd")
  ```

#### **10. Package Management**

- **List installed packages:**
  ```R
  installed.packages()
  ```

- **Update packages:**
  ```R
  update.packages()
  ```

- **Remove a package:**
  ```R
  remove.packages("package_name")
  ```

- **Check for package updates:**
  ```R
  old.packages()
  ```

- **Install package from GitHub:**
  ```R
  install.packages("devtools")
  devtools::install_github("username/repository")
  ```

#### **11. Parallel Computing**

- **Install parallel package:**
  ```R
  install.packages("parallel")
  library(parallel)
  ```

- **Parallel apply:**
  ```R
  mclapply(1:10, function(x) x^2, mc.cores = 4)
  ```

- **Parallel map with `furrr`:**
  ```R
  install.packages("furrr")
  library(furrr)
  plan(multiprocess, workers = 4)
  future_map(1:10, ~ .x^2)
  ```

#### **12. Working with Databases**

- **Install database packages:**
  ```R
  install.packages(c("DBI", "RSQLite", "dplyr"))
  library(DBI)
  library(RSQLite)
  library(dplyr)
  ```

- **Connect to SQLite database:**
  ```R
  con <- dbConnect(RSQLite::SQLite(), "database.sqlite")
  ```

- **List tables:**
  ```R
  dbListTables(con)
  ```

- **Read table into data frame:**
  ```R
  data <- dbReadTable(con, "table_name")
  ```

- **Write data frame to table:**
  ```R
  dbWriteTable(con, "table_name", data)
  ```

- **Execute SQL query:**
  ```R
  result <- dbGetQuery(con, "SELECT * FROM table_name WHERE column_name = 'value'")
  ```

- **Disconnect from database:**
  ```R
  dbDisconnect(con)
  ```

#### **13. Machine Learning**

- **Install caret package:**
  ```R
  install.packages("caret")
  library(caret)
  ```

- **Train-test split:**
  ```R
  set.seed(123)
  trainIndex <- createDataPartition(data$target, p = 0.8, list = FALSE)
  trainData <- data[trainIndex,]
  testData <- data[-trainIndex,]
  ```

- **Train model:**
  ```R
  model <- train(target ~ ., data = trainData, method = "rpart")
  ```

- **Make predictions:**
  ```R
  predictions <- predict(model, testData)
  ```

- **Evaluate Model:**
  ```R
  confusionMatrix(predictions, testData$target)
  ```

### **Advanced Techniques in R**

#### **14. Functional Programming**

- **Anonymous functions:**
  ```R
  sapply(1:10, function(x) x^2)
  ```

- **Apply family functions:**
  ```R
  lapply(data, mean)
  sapply(data, mean)
  apply(matrix_data, 1, sum)
  ```

- **Higher-order functions with purrr:**
  ```R
  install.packages("purrr")
  library(purrr)
  map(1:10, ~ .x^2)
  ```

#### **15. Advanced Data Wrangling with tidyr**

- **Install tidyr:**
  ```R
  install.packages("tidyr")
  library(tidyr)
  ```

- **Gather (wide to long format):**
  ```R
  long_data <- gather(data, key = "variable", value = "value", -id)
  ```

- **Spread (long to wide format):**
  ```R
  wide_data <- spread(long_data, key = "variable", value = "value")
  ```

- **Separate columns:**
  ```R
  separated_data <- separate(data, col = "column_name", into = c("col1", "col2"), sep = "_")
  ```

- **Unite columns:**
  ```R
  united_data <- unite(data, new_column, col1, col2, sep = "_")
  ```

#### **16. Shiny Web Applications**

- **Install Shiny:**
  ```R
  install.packages("shiny")
  library(shiny)
  ```

- **Create Shiny app:**
  ```R
  ui <- fluidPage(
    titlePanel("Simple Shiny App"),
    sidebarLayout(
      sidebarPanel(
        sliderInput("bins", "Number of bins:", min = 1, max = 50, value = 30)
      ),
      mainPanel(
        plotOutput("distPlot")
      )
    )
  )

  server <- function(input, output) {
    output$distPlot <- renderPlot({
      x <- faithful$eruptions
      bins <- seq(min(x), max(x), length.out = input$bins + 1)
      hist(x, breaks = bins, col = 'darkgray', border = 'white')
    })
  }

  shinyApp(ui = ui, server = server)
  ```

#### **17. Advanced Plotting with Plotly**

- **Install Plotly:**
  ```R
  install.packages("plotly")
  library(plotly)
  ```

- **Create interactive plot:**
  ```R
  plot_ly(data, x = ~column1, y = ~column2, type = 'scatter', mode = 'lines+markers')
  ```

- **3D plot:**
  ```R
  plot_ly(data, x = ~column1, y = ~column2, z = ~column3, type = 'scatter3d', mode = 'markers')
  ```

#### **18. Reproducible Research with knitr**

- **Install knitr:**
  ```R
  install.packages("knitr")
  library(knitr)
  ```

- **Knit R Markdown to HTML:**
  ```R
  knit("report.Rmd")
  ```

- **Embed R code in Markdown:**
  ```markdown
  ```{r}
  summary(data)
  ```
  ```

#### **19. Debugging and Profiling**

- **Debug a function:**
  ```R
  debug(function_name)
  function_name(args)
  undebug(function_name)
  ```

- **Profiling code with Rprof:**
  ```R
  Rprof("profile_data.out")
  # Your code here
  Rprof(NULL)
  summaryRprof("profile_data.out")
  ```

- **Advanced debugging with `debugger`:**
  ```R
  install.packages("debugger")
  library(debugger)
  mdebug(function_name)
  ```

#### **20. Working with APIs**

- **Install httr package:**
  ```R
  install.packages("httr")
  library(httr)
  ```

- **GET request:**
  ```R
  response <- GET("https://api.example.com/data")
  content <- content(response, "text")
  ```

- **POST request:**
  ```R
  response <- POST("https://api.example.com/data", body = list(key = "value"))
  content <- content(response, "text")
  ```

- **JSON parsing:**
  ```R
  install.packages("jsonlite")
  library(jsonlite)
  json_data <- fromJSON(content)
  ```

#### **21. Parallel Processing with future and furrr**

- **Install future and furrr:**
  ```R
  install.packages(c("future", "furrr"))
  library(future)
  library(furrr)
  ```

- **Set up parallel plan:**
  ```R
  plan(multisession, workers = 4)
  ```

- **Parallel mapping:**
  ```R
  results <- future_map(1:10, ~ .x^2)
  ```

- **Shut down parallel workers:**
  ```R
  plan(sequential)
  ```

#### **22. Advanced Machine Learning with caret**

- **Preprocessing data:**
  ```R
  preProc <- preProcess(trainData, method = c("center", "scale"))
  trainData <- predict(preProc, trainData)
  testData <- predict(preProc, testData)
  ```

- **Cross-validation:**
  ```R
  trainControl <- trainControl(method = "cv", number = 10)
  model <- train(target ~ ., data = trainData, method = "rpart", trControl = trainControl)
  ```

- **Hyperparameter tuning:**
  ```R
  grid <- expand.grid(cp = seq(0.01, 0.1, by = 0.01))
  model <- train(target ~ ., data = trainData, method = "rpart", trControl = trainControl, tuneGrid = grid)
  ```

#### **23. Text Mining and Natural Language Processing**

- **Install text mining packages:**
  ```R
  install.packages(c("tm", "SnowballC"))
  library(tm)
  library(SnowballC)
  ```

- **Create corpus:**
  ```R
  docs <- Corpus(VectorSource(text_data))
  ```

- **Text preprocessing:**
  ```R
  docs <- tm_map(docs, content_transformer(tolower))
  docs <- tm_map(docs, removePunctuation)
  docs <- tm_map(docs, removeNumbers)
  docs <- tm_map(docs, removeWords, stopwords("en"))
  ```

- **Term-document matrix:**
  ```R
  dtm <- DocumentTermMatrix(docs)
  ```

- **Word cloud:**
  ```R
  install.packages("wordcloud")
  library(wordcloud)
  wordcloud(words = names(freq), freq = freq, min.freq = 1, scale = c(3, 0.5))
  ```

- **Sentiment analysis with `syuzhet`:**
  ```R
  install.packages("syuzhet")
  library(syuzhet)
  sentiments <- get_nrc_sentiment(text_data)
  ```

#### **24. Advanced Data Management with data.table**

- **Install data.table:**
  ```R
  install.packages("data.table")
  library(data.table)
  ```

- **Convert data frame to data.table:**
  ```R
  dt <- as.data.table(data)
  ```

- **Fast data filtering:**
  ```R
  filtered_data <- dt[column_name == "value"]
  ```

- **Fast aggregation:**
  ```R
  aggregated_data <- dt[, .(mean_value = mean(column_name)), by = group_column]
  ```

- **Joining tables:**
  ```R
  merged_data <- merge(dt1, dt2, by = "common_column")
  ```

### **Summary**

This extensive list provides a comprehensive overview of R CLI commands and advanced techniques across various domains, including data manipulation, visualization, statistical analysis, machine learning, parallel computing, and more. It covers basic operations, package management, advanced data wrangling with dplyr and tidyr, web applications with Shiny, interactive plotting with Plotly, reproducible research with knitr, debugging, working with APIs, and advanced machine learning with caret, among other topics.  
