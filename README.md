# babys
<!-- R Commander Markdown Template -->

computación estadistica
=======================

### Usuario

### `r as.character(Sys.Date())`

```{r echo=FALSE}
# incluya este fragmento de código literalmente para especificar las opciones
knitr::opts_chunk$set(comment=NA, prompt=TRUE, out.width=750, fig.height=8, fig.width=8)
library(Rcmdr)
library(car)
library(RcmdrMisc)
```


### Test de correlación: fnocig, mnocig
```{r}
with(INFERENCIAL, cor.test(fnocig, mnocig, alternative="two.sided", 
  method="pearson"))
```


### Modelo lineal: RegModel.1: Birthweight~Gestation
```{r}
RegModel.1 <- lm(Birthweight~Gestation, data=INFERENCIAL)
summary(RegModel.1)
```

```{r}
INFERENCIAL <- within(INFERENCIAL, {
  race <- factor(race, labels=c('Blanca','Negra','Latina','Asiatica'))
})
```


### Test de Normalidad: Gestation ~ race
```{r}
normalityTest(Gestation ~ race, test="shapiro.test", data=INFERENCIAL)
```


### Test de Normalidad: Gestation ~ race
```{r}
normalityTest(Gestation ~ race, test="shapiro.test", data=INFERENCIAL)
```

```{r}
INFERENCIAL <- within(INFERENCIAL, {
race <- factor(race, labels=c('Blanca','Negra','Latina','Asiatica'))
})
```



### Test de Bartlett Gestation ~ race
```{r}
Tapply(Gestation ~ race, var, na.action=na.omit, data=INFERENCIAL) 
  # variances by group
bartlett.test(Gestation ~ race, data=INFERENCIAL)
```

```{r}
library(mvtnorm, pos=17)
```


```{r}
library(survival, pos=17)
```


```{r}
library(MASS, pos=17)
```


```{r}
library(TH.data, pos=17)
```


```{r}
library(multcomp, pos=17)
```


```{r}
library(abind, pos=22)
```



### Analisis de varianza de un factor: Gestation ~ race
```{r}
AnovaModel.2 <- aov(Gestation ~ race, data=INFERENCIAL)
summary(AnovaModel.2)
with(INFERENCIAL, numSummary(Gestation, groups=race, statistics=c("mean", 
  "sd")))
```

