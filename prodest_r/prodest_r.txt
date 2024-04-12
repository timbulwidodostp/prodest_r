# Olah Data Semarang
# WhatsApp : +6285227746673
# IG : @olahdatasemarang_
# Production Function Estimation Use Package prodest With (In) R Software
# Production Function Estimation Based On The Control Function Approach Use Package prodest With (In) R Software
# Install Production Function Estimation Use Package prodest With (In) R Software
# Install Production Function Estimation Based On The Control Function Approach Use Package prodest With (In) R Software
install.packages("readxl")
install.packages("httr")
install.packages("prodest")
library(httr)
library("readxl")
library("prodest")
# Import Data Excel Into R From Github Olah Data Semarang (timbulwidodostp)
github_link <- "https://github.com/timbulwidodostp/prodest_r/raw/main/prodest_r/prodest_r.xlsx"
temp_file <- tempfile(fileext = ".xlsx")
req <- GET(github_link, 
# authenticate using GITHUB_PAT
authenticate(Sys.getenv("GITHUB_PAT"), ""),
# write result to disk
write_disk(path = temp_file))
prodest_r <- readxl::read_excel(temp_file)
# Estimate productivity - Levinsohn-Petrin method
LP_model <- prodestLP(prodest_r$Y, fX = prodest_r$fX2, sX = prodest_r$sX, pX = prodest_r$pX, idvar = prodest_r$idvar, timevar = prodest_r$timevar)
LP_model

# Estimate productivity - Olley-Pakes method
OP_model <- prodestOP(prodest_r$Y, fX = prodest_r$fX2, sX = prodest_r$sX, pX = prodest_r$pX, idvar = prodest_r$idvar, timevar = prodest_r$timevar)
OP_model

# Estimate productivity - Ackerberg-Caves-Frazer correction
ACF_model <- prodestACF(prodest_r$Y, fX = prodest_r$fX2, sX = prodest_r$sX, pX = prodest_r$pX, idvar = prodest_r$idvar, timevar = prodest_r$timevar)
ACF_model

# Estimate productivity - IV Wooldridge method
W_GMM_model<- prodestWRDG(prodest_r$Y, fX = prodest_r$fX2, sX = prodest_r$sX, pX = prodest_r$pX, idvar = prodest_r$idvar, timevar = prodest_r$timevar)
W_GMM_model

# Production Function Estimation Use Package prodest With (In) R Software
# Production Function Estimation Based On The Control Function Approach Use Package prodest With (In) R Software
# Olah Data Semarang
# WhatsApp : +6285227746673
# IG : @olahdatasemarang_
# Finished