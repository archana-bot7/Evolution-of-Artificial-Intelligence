# DAX Measures

The report contains five DAX measures.

## 1. AI Adoption YoY Growth %

```DAX
AI Adoption YoY Growth % =
VAR CurrentYear =
    MAX('The Rise Of Artificial Intellegence2 (1)'[Year])
VAR CurrentAdoption =
    CALCULATE(
        AVERAGE('The Rise Of Artificial Intellegence2 (1)'[AI Adoption (%)])
    )
VAR PreviousAdoption =
    CALCULATE(
        AVERAGE('The Rise Of Artificial Intellegence2 (1)'[AI Adoption (%) ]),
        'The Rise Of Artificial Intellegence2 (1)'[Year] = CurrentYear - 1
    )
RETURN
DIVIDE(
    CurrentAdoption - PreviousAdoption,
    PreviousAdoption,
    0
)
```

Compares the current year's average AI adoption with the previous year.

## 2. Avg AI Adoption Rate

```DAX
Avg AI Adoption Rate =
AVERAGE('The Rise Of Artificial Intellegence2 (1)'[AI Adoption (%)])
```

Calculates average AI adoption across the available years.

## 3. Job Displacement Rate

The report documents the following measure exactly as written in Power BI:

```DAX
Job Displacement Rate =
VAR LatestYear =
    MAX('The Rise Of Artificial Intellegence2 (1)'[Year])
VAR JobsEliminated =
    CALCULATE(
        SUM('The Rise Of Artificial Intellegence2 (1)'[Estimated Jobs Eliminated by AI (millions)]),
        'The Rise Of Artificial Intellegence2 (1)'[Year] = LatestYear
    )
VAR JobsCreated =
    CALCULATE(
        SUM('The Rise Of Artificial Intellegence2 (1)'[Estimated Jobs Eliminated by AI (millions)]),
        'The Rise Of Artificial Intellegence2 (1)'[Year] = LatestYear
    )
RETURN
DIVIDE(
    JobsEliminated,
    JobsCreated + JobsEliminated,
    0
)
```

**Important:** The report explicitly notes that `JobsCreated` references the Jobs Eliminated column in the Power BI version, rather than the Jobs Created column. This documentation preserves the report's formula exactly.

## 4. Net Job Impact (M)

```DAX
Net Job Impact (M) =
SUM('The Rise Of Artificial Intellegence2 (1)'[Estimated New Jobs Created by AI (millions)])
-
SUM('The Rise Of Artificial Intellegence2 (1)'[Estimated Jobs Eliminated by AI (millions)])
```

Calculates total jobs created minus total jobs eliminated, in millions.

## 5. Total Market Value (B)

```DAX
Total Market Value (B) =
SUM('The Rise Of Artificial Intellegence2 (1)'[Global AI Market Value(in Billions)])
```

Adds the global AI market value across the available years, in billions.
