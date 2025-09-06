This project explores flight delay prediction using the 2019 Airline Delays with Weather and
Airport Detail dataset. Our goal is to identify which flight, weather, and airport-related features
contribute most to delays. We applied Linear Discriminant Analysis (LDA), Quadratic
Discriminant Analysis (QDA), and Principal Component Analysis (PCA) to model the delay
status (Delayed vs On-Time), comparing their effectiveness. The study highlights the importance
of feature selection, data balancing, and limitations due to missing real-world delay causes in
the dataset.

**Data Overview:**
The dataset used for this project is the 2019 Airline Delays with Weather and Airport Detail
dataset, which contains comprehensive flight and weather information. It includes categorical
and continuous variables and spans multiple files: Combined_Flights_Weather.csv (about 5.8
million records), Airlines.csv, Airports.csv, and Weather.csv. Key data elements cover flight
identifiers, airport information, scheduled and actual flight times, meteorological data such as
temperature, wind speed, precipitation, and visibility, as well as binary indicators showing
whether a flight was delayed. This variety of features enables an integrated approach to
analyzing flight delays.

**Data Preprocessing:**
To narrow the scope and ensure manageable analysis, we selected a subset of flights operated
by Southwest Airlines. This airline was chosen for its large volume of flights, providing a
sufficient sample size while allowing for focused exploration of patterns related to delay
prediction.

**Handling Missing Values:**
Rows with missing values in key features, such as weather variables, DelayStatus, and aircraft
information, were removed to maintain data integrity. The size of the dataset allowed us to
safely drop incomplete records without major loss of representativeness.

**Feature Selection:**
From the full set of flight and weather variables, we selected predictors that were relevant,
variable, and non-redundant. Columns with no variation or highly similar values were dropped.
Final selected features included month, day of week, flight distance group, concurrent flights at
the airport, average monthly passengers, and weather-related fields such as precipitation,
snowfall, temperature, and wind speed.

EDA
a. Boxplots:
Boxplots revealed slight differences in certain features across delayed and on-time flights.
Delayed flights tended to show marginally higher wind speed (AWND) and greater plane age.
PRCP and SNOW were mostly zero across the dataset but did appear slightly more in delayed
flights. TMAX (maximum temperature) distributions were similar across both classes, suggesting
minimal effect on delays.

b. Correlation Matrix:
A correlation matrix of numerical features confirmed weak correlations across most variables.
TMAX and SNOW had a mild negative relationship (-0.24), indicating colder days were
associated with snow. Most other features appeared largely independent, reducing redundancy
and supporting the inclusion of all selected variables in the models.

LDA (Linear Discriminant Analysis):
LDA was highly conservative in its predictions. It identified only one flight as delayed, but did so
with perfect precision. As a result, LDA achieved a high accuracy of 83.27% and a specificity of
100%, but its sensitivity (recall) was extremely low at 1.67%. This made it ineffective for
identifying most delay cases, even though its predictions for on-time flights were highly
accurate. The confusion matrix for LDA shows 59 false negatives and only 1 true positive.
QDA (Quadratic Discriminant Analysis):
QDA performed better in terms of sensitivity, correctly identifying 23.33% of delayed flights. It
achieved balanced accuracy (54.97%) and was more realistic for detecting delays despite a
lower overall accuracy of 70.91%. QDA had a better balance between identifying true delays
and avoiding excessive false positives. The confusion matrix for QDA indicates 14 true positives
and 32 false positives, with 207 correct on-time predictions.

Output Analysis:
Based on model outputs, LDA was more precise but missed nearly all delays, while QDA better
detected delays at the expense of accuracy. LDA had high accuracy and specificity but poor
recall. QDA had a better balance between sensitivity and specificity, suggesting it is more
practical when detecting delays is prioritized. PCA helped in feature visualization but did not
enhance prediction performance.

8. Conclusion:
This study showed that using a limited set of features (weather, flight timing, and airport activity),
both LDA and QDA struggled to effectively predict flight delays. LDA was more precise for
on-time predictions, while QDA captured more delays but at the cost of false alarms. More
operational and historical data is needed for stronger performance.

10. Challenges:
We faced several challenges during this project. First, the original dataset was extremely large,
requiring downsampling for practical analysis. Second, the data was imbalanced—most flights
were on time. Third, many features showed little or no variation, offering little modeling value.

Finally, some critical real-world delay causes—such as crew scheduling, connecting flights,
mechanical issues, and airport congestion—were missing.
These missing features limited the model’s ability to capture real-world delay causes. Important
factors not included in the dataset were:
●
Crew arrival delays
●
Gate availability or maintenance
●
Connecting passenger and luggage delays
●
Ground operations issues (fueling, catering)
●
Previous flight delays (domino effects)
As a result, predictions were weaker than they could be with more operational data.
