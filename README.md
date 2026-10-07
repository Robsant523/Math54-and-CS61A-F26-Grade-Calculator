# Course Grade Planner

A single-file, interactive grade calculator for **CS 61A** and **Math 54**. Enter actual and projected scores to estimate your course grade and the final-exam score needed to reach your target.

The interface is inspired by the [CS 61A Fall 2026 website](https://cs61a.org/fa26/). This is a personal planning tool, not an official course gradebook.

## Getting started

1. Download or locate `course-grade-planner.html`.
2. Open it in a modern web browser.
3. Select **CS61A** or **Math 54** in the course navigation.
4. Replace the example scores with your earned scores and estimates for unfinished work.
5. Choose a target grade and review **Final exam needed**. Use the final-exam input or slider to explore other outcomes.

No installation, server, account, or internet connection is required for the calculators. The external course website link requires internet access.

## Features

- Separate course calculators in one HTML file.
- Immediate updates when scores change.
- Target-grade and final-exam scenario calculations.
- Optional individual quiz and homework entry where supported.
- Input validation, keyboard-accessible course tabs, and a responsive layout.
- Inputs remain in place when switching courses during the same page session.

**Scores are not saved across reloads or closing the page.** Default values are examples, not your actual grades.

## CS 61A

### Point system

| Category | Maximum points |
| --- | ---: |
| Midterm 1 | 20 |
| Midterm 2 | 20 |
| Midterm 3 | 45 |
| Final exam | 75 |
| Quizzes | 10 |
| Homework | 10 |
| Four projects combined | 100 |
| Lab | 10 |
| Discussion | 10 |
| **Regular total** | **300** |
| Early project submission extra credit | **4 additional** |

Enter the expected final total for each coursework category. For quizzes, enter the total out of 10 or enable individual percentage scores for all eight quizzes; the calculator uses the best five, assuming equal weighting. Lab 0 and Discussion 0 do not count.

### Exam recovery

When recovery is enabled, each midterm receives the greater of its original score and 90% of the final-exam percentage applied to that midterm's maximum:

```text
adjusted midterm = max(original midterm, 0.9 × final / 75 × midterm maximum)
```

Recovery applies only when taking the final during finals week, without an incomplete. Disable it when ineligible.

### Grade thresholds and rounding

| Grade | Points after rounding |
| --- | ---: |
| A | 285 |
| A− | 270 |
| B+ | 255 |
| B | 230 |
| B− | 210 |
| C+ | 190 |
| C | 180 |
| C− | 175 |
| D+ | 170 |
| D | 165 |
| D− | 160 |

The final course total rounds to the nearest integer, with half points rounding up. An A therefore requires at least **284.5 raw points**. The calculator solves for the required final score with recovery included and rounds the displayed requirement upward to 0.01 points. It also shows the minimum whole-point final score.

A+ qualification uses a separate points system and is not calculated.

## Math 54

### Two grading methods

| Component | Method 1 | Method 2 |
| --- | ---: | ---: |
| Homework | 7% | 7% |
| Quizzes | 13% | 13% |
| Midterm 1 | 22% | — |
| Midterm 2 | 22% | — |
| Better midterm | — | 30% |
| Final exam | 36% | 50% |

Both methods are calculated and the higher course grade is used.

- **Homework:** enter the best-11 average as a percentage, or enter all 13 assignment percentages and enable automatic selection of the best 11.
- **Quizzes:** enter the best-seven average **out of 6**, or enter all 10 quiz scores on the **0–6 scale** and enable automatic selection of the best seven. The retained average is converted to a percentage for weighting.
- Individual assignment calculations assume equal weighting within each category. Use the course-reported average if its weighting differs.
- **Exams:** enter percentages after any course adjustment. The adjustment formulas were missing from the supplied policy, so the calculator does not apply or reverse the exam curve. You may use raw percentages to explore an uncurved scenario.

### Extra credit

Poll Everywhere credit, when enabled, adds:

- 0 percentage points for participation at or below 40%.
- A proportional amount between 40% and 60% participation; for example, 50% participation gives +0.5 percentage points.
- 1 percentage point at or above 60% participation.

The course-evaluation checkbox adds another percentage point when at least 75% of the class completes the evaluation. Extra credit is added to each weighted course average.

### Approximate cutoffs

| Grade | Course percentage |
| --- | ---: |
| A+ | 98 |
| A | 93 |
| A− | 90 |
| B+ | 87 |
| B | 83 |
| B− | 80 |
| C+ | 77 |
| C | 73 |
| C− | 70 |
| D+ | 67 |
| D | 63 |
| D− | 60 |
| F | Below 60 |

The target cutoff is editable. Editing it changes the target calculation; the displayed letter-grade estimate continues to use the table above. The instructor finalizes the actual cutoffs at the end of the semester.

Required final percentages are rounded upward to 0.01%. No course-grade rounding policy was supplied for Math 54, so none is applied when determining the estimated letter grade. The required final percentage is an **adjusted exam percentage**, not a prediction of the raw exam score needed before a curve.

## Limitations

- Results depend on the actual and projected scores entered and the supplied grading policies.
- A target can be unreachable under the current assumptions, even with a perfect final.
- A mathematical requirement of zero does not waive exam attendance or other course requirements.
- Displayed values may be rounded for readability; course scoring increments can affect the attainable minimum.
- Check the syllabus or instructor announcements for policy changes.

## Editing the file

All HTML, CSS, and JavaScript are embedded in `course-grade-planner.html`. There are no third-party runtime dependencies or build steps.

- Edit the `<style>` block to change the appearance.
- The calculators use separate function scopes and course-prefixed element IDs to keep their inputs independent.
- Course navigation switches panels without reloading them.
- In browsers supporting `document.modelContext`, an optional read-only `read_grade_estimates` tool exposes current estimates. Unsupported browsers simply skip registration.

After changing grading logic, check target boundaries, recovery, both Math 54 methods, quiz conversions, and invalid inputs. After changing layout, check both course tabs at desktop and mobile widths.
