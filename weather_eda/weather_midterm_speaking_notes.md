# Midterm speaking notes, weather section (about 3 minutes)

Open `weather_midterm_d3.html` in Chrome, press F11 for full screen, move with the down arrow. Each section is one slide. Numbers in brackets are the rubric lines the slide covers. The page follows the system light or dark theme.

Interactions worth showing live: click a metro row in section 3 or 4 and section 5 switches to that metro; drag the "what if" slider in section 4 to about 50 percent and watch every ratio land on 1; press "Play the months" in section 5; hover a line in section 7 to isolate it.

## Section 1, title (25 seconds) [general task, specific task, audience, data set]

"Our general task as a team is to let a curious non expert explore when, where and how autonomous vehicles crash, using the NHTSA Standing General Order reports. My specific task is weather. The reader should be able to compare crashes across weather conditions and decide whether rain raises the risk, because that is the question regulators and riders actually ask. The data is 2,945 crashes from July 2021 to August 2026, two NHTSA schemas merged and deduplicated. Rain is 114 of them, 3.9 percent, and it is the only adverse condition with enough cases to test."

## Section 2, iteration (35 seconds) [how much iteration, how reasonable the choices]

"This strip is the five versions of the chart, all drawn from the real data. Step one, raw counts of eight weather codes, is unreadable and has no denominator. Step two normalizes per metro: rain is one to six percent everywhere, and the order of the cities is the order of how rainy they are. That told me counts could never answer the question, so step three adds exposure, the share of hours it actually rained in each metro from a weather archive. That is the step where the hypothesis flipped. Step four adds intervals so we can tell evidence from noise, and step five checks the pattern month by month."

## Section 3, dumbbell (40 seconds) [types of visualization, examples of insight, supporting text]

Click "Crash share in rain" first, then "Add how often it rains" while talking.

"Here is the main view. The blue dot is the share of a metro's crashes that happened in rain. Now I add the gray dot, how often it rains there. If rain were neutral the dots would sit on top of each other. In every metro the blue dot is to the left. Austin and Atlanta, the rainiest cities, have the biggest gaps: Atlanta gets rain 16 percent of the time and 6 percent of its crashes. A dumbbell rather than two bars because the gap is the object we want people to see, and the metros are sorted by exposure so the eye reads a trend."

## Section 4, ratio with intervals (30 seconds) [insight, reasonable choices]

"One number per metro: crash share divided by rain share, so one means neutral. Everything is below one, between 0.38 and 0.63, and the four metros with the most data have intervals that exclude one. Las Vegas has one rain crash, so its interval runs off the chart; we show that rather than hide it. Without intervals Atlanta looks like the strongest evidence; with them San Francisco is, because it has 48 rain crashes behind it."

Drag the slider to 50 percent: "The reports have no miles. If fleets drove only half their usual miles in rain, every metro would land on one. That is the exposure explanation, and it is why the next data we want is miles."


## Section 5, month by month (25 seconds) [iteration, appropriate type]

Toggle to "all crashes" mid sentence. If time allows, click Austin or LA to show the same shape in a second metro.

"Is this an averaging artifact? In San Francisco rain crashes rise and fall with the wet winters, r of 0.56. Switch to all crashes and the correlation disappears; total crashes track how many vehicles were on the road. My first version was a dual axis chart and the course was right that it says nothing; two panels sharing a time axis is clearer."

## Section 6, severity (15 seconds) [insight]

"Could rain crashes be rarer but worse? No. Injury rates are 10 percent clear, 8 cloudy, 7 rain, and dry and wet roads are identical. Nothing points up in rain."

## Section 7, crash partner (10 seconds) [insight, honest labeling]

"What rain does change is who the vehicle hits: more fixed objects and passenger cars, fewer SUVs and trucks. With 114 rain crashes that is a hint, not a finding, and the chart says so."

## Section 8, conclusion and plan (30 seconds) [testing plan, mockup completeness, understanding of tasks]

"So the hypothesis is rejected, and the most likely reason is exposure: fleets drive fewer miles in rain, by demand and by operator policy, and the reports contain no miles, so we cannot yet separate safer in rain from absent in rain. For the final, weather becomes a filter and seasonal context rather than a headline number, every rate gets a denominator and an interval, and these three D3 components become the building blocks with a metro selector. Testing: five think aloud sessions with non experts, three tasks, success is a correct answer in under twenty seconds, and we retest after fixing the two worst labels. The next data we want is Waymo's rider only miles by city and month, which would turn the ratio into a true crash rate."

## If asked

- Why Wilson and not a normal interval: small counts (one rain crash in Las Vegas); Wilson stays inside zero to one and does not collapse to zero width.
- Why treat exposure as known: it comes from hourly weather for the whole metro, thousands of hours, so its sampling error is tiny next to the crash counts.
- Why not a map: the question is rain versus no rain within a city, not between cities; a map would turn into a map of where the fleets operate.
- Operators: Avride and Aurora look rain prone pooled, but they operate in Texas; inside any one city every operator sits below the exposure line.
- Time zone and reporting: the SGO weather field is a tick box at report time; "cloudy" versus "clear" is subjective, which is why rain is the only category we lean on.
