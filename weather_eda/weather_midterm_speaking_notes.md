# Midterm speaking notes, weather section (about 3 minutes)

Open `weather_midterm_d3.html` in Chrome, press F11 for full screen, move with the down arrow. The page follows the system light or dark theme; dark looks best on a projector. Numbers in brackets are the rubric lines the slide covers.

Live interactions worth showing: hover any dot in the opening section (every dot is a real report with city, date, operator, partner, severity); click a metro in section 3 or 5 and sections 4 to 6 follow it; press Run in section 4; drag the slider in section 5 to about 50 percent; press Play in section 6; hover a line in section 8.

## Section 1, the dots (60 seconds, five screens) [general task, specific task, audience, data set, insight]

Screen 1, title: "Every dot is one crash report filed with NHTSA for an automated driving system, 2,945 of them from July 2021 to August 2026. Color is the weather box the operator ticked. Our team task is to let a curious non expert explore when, where and how these vehicles crash. My task is weather: can a reader compare crash rates across conditions and judge whether rain raises the risk, because that is what regulators and riders actually ask."

Screen 2, by weather: "114 of them, 3.9 percent, were in rain. Fog, snow and wind together are six, so rain is the only adverse condition we can test. On its own 3.9 percent says nothing. It is what you would expect in cities where it rarely rains."

Screen 3, by metro: "Six metros carry 82 percent of the reports, San Francisco alone 1,109. Metros are the right unit because that is where crashes and weather can be measured over the same months."

Screen 4, rings: "Now each metro's crash count times the share of hours it was raining there, from an hourly weather archive. Each ring is a rain crash the weather would predict. The filled dots are the ones that were reported. 187 predicted, 91 reported, and every metro has empty rings. This is where the hypothesis flipped."

Screen 5, hour of day: "Stacked by hour you see the fleet's working day, and rain crashes sit on the same curve with a slight lean to the evening. 114 cases, so that is a hint, not a finding."

## Section 2, iteration (25 seconds) [how much iteration, how reasonable the choices]

"Five versions, all drawn from the real data. Raw counts had no denominator. Shares per metro showed rain at one to six percent in the order of how rainy the cities are, which pointed at exposure. Adding exposure flipped the hypothesis. Intervals separated evidence from noise, and the monthly view checked it was not an averaging artifact."

## Section 3, dumbbell (25 seconds) [types of visualization, insight, supporting text]

Click "Add how often it rains" while talking.

"The analytic version of the rings. Blue is the share of a metro's crashes in rain, gray is how often it rains there. If rain were neutral they would sit on top of each other. Blue is left of gray in every metro, and the gap is largest in Austin and Atlanta, the rainiest cities. A dumbbell rather than two bars because the gap is the object."

## Section 4, simulation (25 seconds) [reasonable choices, insight]

Press Run.

"Could this be chance? We rerun the world a thousand times keeping every metro's crash count and rain hours, letting each crash fall in rain purely by chance. The worlds land between about 150 and 230 rain crashes. The real count is 91. No world gets near it. Pick Las Vegas and you see the other side: one rain crash tells you nothing, which is what its wide interval means on the next slide."

## Section 5, ratio with intervals and the slider (20 seconds) [insight]

Drag the slider to 50 percent.

"One number per metro: 0.38 to 0.63 of what rain would predict, four intervals exclude one. The reports contain no miles. If fleets drove half their usual miles in rain, every metro would land on one. That is the exposure explanation, and it is why the next data we want is miles."

## Section 6, small multiples (20 seconds) [iteration, appropriate type]

Toggle to "all crashes" mid sentence, or press Play.

"Month by month, one panel per metro, gray bars are rain hours and each blue dot is a rain crash. In San Francisco the dots pile up under the wet winters, r of 0.56. Switch to all crashes and it disappears; totals track the size of the fleet. My first version was a dual axis chart of one city. Six panels on one time axis say more with less."

## Section 7, severity (10 seconds) [insight]

"Rarer but worse? No. Ten percent of clear weather crashes injure someone, seven percent of rain crashes, and dry and wet roads are identical."

## Section 8, crash partner (10 seconds) [insight, honest labeling]

"What rain does change is who the vehicle hits: more fixed objects and passenger cars, fewer SUVs and trucks. Labeled as a hint."

## Section 9, conclusion and plan (25 seconds) [testing plan, mockup completeness, understanding of tasks]

"Hypothesis rejected; the likely reason is exposure, and we cannot separate safer in rain from absent in rain until we have miles. For the final, weather becomes a filter and seasonal context, the dot stays the unit so every percentage can dissolve back into reports, every rate gets a denominator and an interval, and these D3 components are already linked by one metro selection. Testing: five think aloud sessions with non experts, three tasks, success is a correct answer under twenty seconds, then we rewrite the two worst labels and retest."

## If asked

- Why Wilson and not a normal interval: small counts (one rain crash in Las Vegas); Wilson stays inside zero to one and does not collapse to zero width.
- Why the simulation and the interval both: same model (binomial per metro). The simulation is for readers who do not know the word interval; the interval is for the ones who do.
- Why treat exposure as known: it comes from hourly weather for the whole metro, thousands of hours, so its sampling error is tiny next to the crash counts.
- Why canvas for the dots and SVG for the charts: 2,945 animated dots with hover need canvas and a quadtree; the analytic charts need text, axes and transitions, which SVG does well.
- Why not a map: the question is rain versus no rain within a city, not between cities; a map would turn into a map of where the fleets operate.
- Operators: Avride and Aurora look rain prone pooled, but they operate in Texas; inside any one city every operator sits below the exposure line.
- Weather field quality: it is a tick box at report time; cloudy versus clear is subjective, which is why rain is the only category we lean on.
