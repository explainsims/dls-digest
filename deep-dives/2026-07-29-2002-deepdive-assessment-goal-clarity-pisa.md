# The 152,000-Student Assessment Study: What It Measured, What the Press Release Turned It Into, and What Breaks When AI Arrives

_Filed 29 July 2026._

> **Thesis:** The study is real, the analysis is competent, and the headline is wrong in a specific and instructive way. The paper does not find that feedback lowers achievement. It finds that the *unevenness* of feedback across students within a school is negatively associated with reading scores, while the *amount* of feedback is not significantly associated with anything once other factors are controlled. The positive finding — "clarity of learning goals" — is not a school policy variable at all; it is a school-level average of what students say their own teachers do, and the four items behind it look more like teacher-directed instruction than like assessment criteria. On a common scale the headline lever is about the size of the boy/girl reading gap in the same model, and roughly a quarter the size of schoolmates' socio-economic status. All of it rests on 2018 data, which is the last cycle before generative AI touched a single assessed piece of student work — and the one construct AI most directly rewrites is the one the paper got wrong.

## 1. What the study actually is

The paper is Zi Yan, Ming Ming Chiu, Jiahe Gu, Lan Yang and Ying Zhan, "School Assessment Policy, Teacher Assessment Practice and Training, and Reading Achievement: A Multi-Level Analysis of PISA 2018 Data", *Education Sciences* 16(4), 658 — submitted 5 March 2026, accepted 15 April, published 20 April ([doi:10.3390/educsci16040658](https://doi.org/10.3390/educsci16040658)). All five authors are at The Education University of Hong Kong; the work received no external funding. It reached the wires three months later via an EdUHK release on 21 July ([EurekAlert](https://www.eurekalert.org/news-releases/1137068)) and was picked up on 23 July ([Phys.org](https://phys.org/news/2026-07-explore-classroom-applications-ai-platforms.html)).

The design is a three-level regression — students within schools within countries — on PISA 2018 reading scores. The sample is 151,969 fifteen-year-olds in 5,225 schools across 19 systems: the United States, Brazil, Chile, the Dominican Republic, Panama, Peru, Chinese Taipei, Hong Kong, Korea, Macau, Malaysia, Germany, Portugal, Spain, the United Kingdom, Morocco, Albania, Baku (Azerbaijan) and the United Arab Emirates. That list is not a design choice so much as an availability constraint: PISA's teacher questionnaire is optional, and these are the systems that ran it. Countries "without assessment-related data were excluded".

Two things follow that no coverage mentioned. First, the sample's mean reading score is 453.5 with a standard deviation of 107.5 — well below the OECD average of 487 for that cycle. Five of the 19 systems are Latin American. Vietnam is absent. So are Singapore, Finland, Japan, Canada, Australia, Estonia and every other system a high-performing international school would naturally benchmark against. Second, the model carries a blunt "Confucian" dummy — Chinese Taipei, Hong Kong, Korea, Macau — worth +56.4 points (SE 18.2) in the final model. Four of nineteen systems are absorbing a coefficient larger than every assessment variable in the paper combined, and the authors concede their own country-level power is weak: "it is low for 19 regions/countries, so the likelihood of a non-significant country/region false negative is high."

Variance decomposition: 50% of the differences in reading achievement sit at the student level, 28% at country level, 23% at school level. The final model explains 38.7% of total variance. The school assessment-policy block added **1%** of that. The formative-assessment block added **2%**.

## 2. "Clearer goals" is not a school policy, and it may not be about goals

This is the first place the press framing detaches from the paper. The release describes "a consistent, school-wide implementation of clear learning goals and progress monitoring". That phrasing implies an institutional policy lever. It is not one.

The paper actually built *two* parallel sets of formative-assessment indices. One from the teacher questionnaire (school means of language teachers' own reports), and one from the student questionnaire, with the same items reworded so "my teacher" replaced "I". It then also computed, for each school, the mean of the student index, the within-school standard deviation of the student index, and the student-minus-teacher difference. That is a dozen candidate variables for three constructs.

In the final model, **the teacher-reported variables are all gone.** Every surviving formative-assessment term is student-perception-derived. The paper says as much in its results: "Student perceptions of their teacher's formative assessment practices were also linked to their reading test scores." So what is being measured is not what schools do, and not even what teachers say they do — it is the school-level average of what fifteen-year-olds report their teachers do.

Now the items. Appendix Table A1 gives "clarifying goals and monitoring progress" as exactly four statements: *I set clear goals for the students' learning* · *I ask questions to check whether students have understood what was taught* · *At the beginning of a lesson, I present a short summary of the previous lesson* · *I tell students what they have to learn.* Response options are never/hardly ever, some lessons, many lessons, every lesson.

Two of those four are not goal clarity in any assessment sense. "A short summary of the previous lesson" is lesson structure. "I tell students what they have to learn" is teacher directedness. In PISA's own instrumentation these items sit close to the teacher-directed-instruction family, and the construct that emerges is better read as *structured, explicit, well-signposted teaching* than as *shared success criteria*. That is still a useful finding. It is a different finding from the one the headline sells, and it points at a different intervention — lesson design rather than rubric design.

Meanwhile the variable that genuinely *is* a school policy about learning-focused assessment — the principal-reported "assessment for learning" index, five yes/no items including *to guide students' learning*, *to monitor the school's progress*, *to identify aspects of instruction or the curriculum that could be improved* and *to adapt teaching to the students' needs* — was **not significant**. The authors report this plainly and flag it as non-support for their own hypothesis H-1a. The one school-policy result that did survive is thinner still: schools that publicly post achievement data scored +3.9 points (SE 1.3), and schools making heavier evaluative use of assessment data scored −6.7 points (SE 1.8).

So the honest one-line version of the school-policy findings is: *assessment policy explained one percent of the variance, and the learning-focused policy did nothing.*

## 3. The feedback finding is not the feedback finding

This is the sharpest error, and it is in the paper itself, not only in the coverage.

Table 4, Model 4 — the final model — contains exactly three student-view terms:

| Variable | Coefficient | SE |
|---|---|---|
| Student views of teacher clarify goals and monitor progress — **school mean** | 58.860 | 3.372 |
| Student views of instructional adjustments — **school mean** | 36.120 | 2.912 |
| Student views of provide feedback — **school standard deviation** | −57.700 | 3.845 |

Read the third row again. The negative feedback coefficient is not on the level of feedback. It is on the **within-school standard deviation** of student-reported feedback frequency — how much students inside the same school differ from one another in how much feedback they say they get. The paper's own results section states it correctly: "students in schools with one standard deviation greater difference in frequency of teacher feedback across students than the mean show lower reading achievement (−57 points)." The school *mean* of student-reported feedback did not survive the model. Neither did the individual student's own feedback score. Neither did the teacher-reported feedback index. Per the paper: "All other explanatory variables and interactions were not significant."

Then the abstract says: "schools mostly using assessment data to evaluate, teachers trained in reading comprehension assessment, or **giving more feedback** had students with lower reading scores." The discussion says: "Students who reported higher teacher feedback frequency had lower reading scores, showing no support for H-2c." The conclusion repeats it: "teachers provided more feedback... students were more likely to have lower reading scores."

Those three sentences describe a coefficient the paper did not estimate. The abstract, discussion and conclusion of this paper contradict its own Table 4. Everything downstream — the release, *Phys.org*, and any staffroom slide that ends up saying "research shows more feedback doesn't work" — inherits the error from the abstract, which is the only part most readers reach.

The defensible claim from this dataset is narrower and more interesting: **once you control for country wealth, culture, student and schoolmate SES, grade, language, discipline and teacher-student relationship, how much feedback a school gives is not associated with reading achievement — but how unequally it distributes that feedback is.**

And even that needs a caveat the paper does not supply. Appendix Table A3 shows the raw bivariate correlation between feedback dispersion and reading score is **+0.06** — positive — and its correlation with school mean SES is +0.21. The strong negative coefficient appears only after the full control set. That is a suppression pattern, and the most obvious mechanical explanation is that within-school variance in reported feedback partly tracks within-school variance in attainment: schools with a wider spread of students produce a wider spread of feedback experiences. The paper's own limitations section reaches for the same reversal on the level term, quoting the OECD's PISA 2015 warning that "the relationship runs not from teaching strategy to student success on the items, but in the opposite direction", and conceding "lower-achieving students likely receive more feedback."

## 4. Putting every effect on a common scale

None of the coverage did this, and it is the step that makes the paper usable. Table 4 reports unstandardised coefficients; Table 3 gives the standard deviation of each predictor and of the outcome (reading SD = 107.482). Multiplying one by the other converts every result into standard-deviation units of reading achievement. These conversions are derived from the published tables, not reported in the paper:

| Effect of a 1 SD change in… | Points | SD of reading |
|---|---|---|
| Grade level (per year) | 38.0 | 0.354 |
| Schoolmates' mean SES | 24.7 | 0.230 |
| **School mean, student-perceived goal clarity / monitoring** | **17.8** | **0.166** |
| Being a girl | 16.3 | 0.152 |
| School mean, student-perceived instructional adjustment | 9.8 | 0.091 |
| School SD of student-perceived feedback | −6.9 | −0.064 |
| School policy: assessment for evaluative purposes | −6.7 | −0.062 |
| School publicly posts achievement data | 3.9 | 0.037 |
| Teacher training included assessment practice | 2.4 | 0.022 |
| Teacher training emphasised reading-comprehension assessment | −2.9 | −0.027 |

Three things fall out.

**The headline lever is the size of the gender gap.** 0.166 SD against 0.152 SD for being female. That is a real association and a modest one, and it is dwarfed by the SES of a student's schoolmates.

**The −57.7 coefficient is much smaller than it looks.** Because the feedback-dispersion variable has a standard deviation of only 0.119, a realistic one-SD move on it is worth −6.9 points, or −0.064 SD. The eye-catching number is an artefact of the variable's scale, not a measure of importance. Anyone quoting "−57 points" without that conversion is overstating the finding by roughly eightfold.

**The 0.158 figure in the press release is not in the paper.** It does not appear anywhere in the published text or tables. The closest reconstruction from the paper's own summary statistics — 58.860 × 0.303 ÷ 107.482 — gives **0.166**. Same ballpark, different number; the gap is presumably a different standardising denominator (PISA's nominal 100-point scale, or a school-level rather than pooled SD), but it cannot be reproduced exactly from what was published. *Phys.org* then mangled the release's already-derived figure into pure circularity: "a 0.158-standard-deviation increase in a consistent, school-wide implementation of clear learning goals and progress monitoring was associated with a 0.158-standard-deviation increase in students' reading achievement." The EurekAlert original is coherent — "a one-standard-deviation increase... correlated with a 0.158-standard-deviation increase" — so the corruption happened in the pickup, not at the university.

## 5. Soft spots in the published paper

The examination turned up more than a framing problem. These are checkable against the article as published.

**The sample size disagrees with itself.** The abstract, introduction and method all say 151,969 students. Table 3 is headed "Summary statistics (N = 151,696)." A transposed pair of digits, uncorrected through peer review, in the number that became the story's headline.

**Appendix Table A2 duplicates a factor's loadings.** The five loadings reported for "Assessment for Learning" — 0.753, 0.472, 0.699, 0.852, 0.900, with standard errors 0.025, 0.022, 0.021, 0.016, 0.015 and uniquenesses 0.433, 0.778, 0.511, 0.274, 0.190 — are reproduced digit-for-digit as the loadings for "Assessment for Evaluative Purposes", a different factor built from different items. One of those two columns is wrong.

**A summary statistic is outside its own stated range.** Table 3 gives the teacher-training variable "…emphasised ways to assess reading comprehension" a mean of 2.318 and SD of 0.449 with a minimum of 0 and maximum of 1. A mean cannot exceed the maximum. The standardised effect for that variable in the table above is therefore the least trustworthy figure in it.

**A scale anomaly sits under the headline construct.** Teacher-reported "learning goals and progress" has a mean of 1.499 on the 1–4 frequency scale, floor-adjacent, while teacher-reported feedback (3.193) and instructional adjustments (3.233) sit near the ceiling. The paper's own commentary — "teacher-reported formative assessment practices are relatively higher than student-reported" — holds for two of the three constructs and is reversed for this one (1.499 teacher vs 1.846 student). Either language teachers across nineteen systems say they hardly ever set learning goals, or that row is miscoded.

**Reliability is thin where it matters.** The accountability composite scored Rc = 0.572 with α = 0.295 and had to be broken into its three yes/no components. Assessment for learning reached α = 0.639, evaluative purposes α = 0.600. The authors acknowledge this: "the methodological limitation involves modest reliability estimates, especially for some school-level policy constructs, which may influence the significant associations identified... requiring the audience to interpret the results cautiously."

None of this makes the study worthless. It makes it a competent secondary analysis with a mis-stated abstract, published on a three-and-a-half-week turnaround from submission to acceptance, in a journal where that turnaround is normal. It should be read at the strength it earns, which is: suggestive, correlational, modest in magnitude, and already contradicted by its own summary.

## 6. The pre-AI point, which is the sharpest part

PISA 2018 was fielded in 2018 and reported in December 2019. ChatGPT was released in November 2022. Every response in this dataset was given by a student and a teacher who had never seen a general-purpose text generator, about a reading assessment whose items assume the text in front of the student is the only text in the room.

The instinct is to say "so it's out of date." That is too easy, and it is wrong about which parts age.

**What survives AI, and gets more important.** The goal-clarity items — *I set clear goals*, *I tell students what they have to learn*, *I check whether students have understood* — describe an act of naming the target. Nothing about generative AI degrades that, and the case for it strengthens: when a submitted product is a weaker signal of the process that produced it, the shared statement of what is being learned is one of the few things left that both parties can hold onto. Same for instructional adjustment (+0.091 SD): changing what you teach next in response to what you just saw is a teacher behaviour AI cannot perform and can only inform.

**What AI breaks outright.** The feedback construct. All three items are volume-and-delivery statements — *I give students feedback on their strengths*, *I tell students in which areas they can still improve*, *I tell students how they can improve their performance* — answered on a frequency scale. In 2018, frequency was a reasonable proxy for teacher effort and attention, because writing comments cost time. In 2026 it is not a proxy for anything. A teacher who runs a class set through a model can max out all three items in an afternoon. Any post-2022 replication using these items would be measuring a different quantity under the same name, and it would be measuring it in the direction of a ceiling.

**The one place the finding actually predicts something about AI.** If the real result is that *dispersion* of feedback is the negative term, then automated feedback is the first technology in the history of schooling that plausibly reduces it. Uneven feedback is a scarcity artefact: the loud student, the borderline grade, the essay marked at 11pm. Machine-generated comment compresses that variance toward zero by construction. On this model's own logic, that should be associated with better outcomes — modestly, around 0.06 SD, and only if the compression is real rather than cosmetic. It is the one genuinely forward-looking claim available from this dataset, and it is available only because the coefficient is on the SD and not the mean. The abstract's misreading hides the single most AI-relevant thing in the paper.

**And the replication is a long way off.** Reading returns as PISA's major domain in 2029 — the nine-year rhythm of 2000, 2009 and 2018 — with mathematics and science as minors, and, pointedly, Media and AI Literacy as the innovative domain ([Teacher Magazine on the PISA 2029 MAIL framework](https://www.teachermagazine.com/au_en/articles/pisa-2029-media-and-ai-literacy-key-concepts-curriculum-links-and-competences)). PISA 2025 was science-major, and the programme moves to a four-year cycle after that collection ([OECD, PISA 2025 Integrated Design](https://www.oecd.org/content/dam/oecd/en/about/programmes/edu/pisa/pisa-database/survey-implementation-tools/pisa-2025/PISA-2025-Integrated-Design.pdf)). So a full reading-major cycle on AI-era cohorts does not exist yet and will not report until around 2030. Anyone waiting for the international-large-scale-assessment answer on AI and reading is waiting four more years for the fieldwork and five for the tables.

## 7. What the wider literature says, including what cuts against

An examination that only confirms its own headline is a press release with footnotes. Three bodies of work bear on this, and they do not all point the same way.

**The feedback-is-variable literature supports the paper's caution but not its wording.** Kluger and DeNisi's foundational meta-analysis of 607 effect sizes across 23,663 observations found an average feedback effect of d = 0.41 while more than a third of feedback interventions *reduced* performance ([Kluger & DeNisi, *Psychological Bulletin* 119(2), 254–284](https://mrbartonmaths.com/resourcesnew/8.%20Research/Marking%20and%20Feedback/The%20effects%20of%20feedback%20interventions.pdf)). Wisniewski, Zierer and Hattie's re-analysis of 435 studies (k = 994, N > 61,000) put educational feedback at d = 0.48 with heterogeneity severe enough that they concluded feedback "cannot be understood as a single consistent form of treatment", with information content the dominant moderator ([*Frontiers in Psychology* 10:3087](https://www.frontiersin.org/journals/psychology/articles/10.3389/fpsyg.2019.03087/full)). Both say the same thing the PISA paper should have said: the variable that matters is what is in the feedback, not how often it arrives. Frequency was never the mechanism, so a null on frequency is not news, and it is certainly not evidence against feedback.

**The formative-assessment literature cuts against the paper's optimistic side too.** Kingston and Nash screened more than 300 studies of K-12 formative assessment and found only 13 with enough information to compute an effect size; the random-effects mean was g = 0.20, with English language arts at 0.32, mathematics at 0.17 and science at 0.09 ([*Educational Measurement: Issues and Practice*, 2011](https://onlinelibrary.wiley.com/doi/abs/10.1111/j.1745-3992.2011.00220.x)). That is an order of magnitude below the 0.4–0.7 figures that circulated for two decades on the strength of Black and Wiliam's narrative review. It also places the PISA paper's 0.166 SD for goal clarity squarely inside the plausible modern range — which is reassuring for the paper's credibility and deflating for its billing. The correct summary of the whole field is not "goals beat feedback." It is "all of these levers are worth roughly a fifth of a standard deviation, and the between-study variance exceeds the between-lever variance."

**The paper's own authors half-concede the point.** In their practical implications they write: "Despite the revealed adverse association with providing teacher feedback, we recommend that teachers adopt all three formative assessment practices in classrooms," citing an umbrella review across 13 meta-analyses in which formative assessment generally helped. Their reconciliation is the most quotable line in the article and the one nobody quoted: "feedback provided without concurrent pedagogical action may be insufficient or even counterproductive." That is a claim about *coupling* — feedback tied to a change in what happens next — and it is consistent with both the instructional-adjustment coefficient (+0.091 SD) and the dispersion coefficient (−0.064 SD). It is also, notably, not a claim the abstract makes.

## 8. What it means for setting up assessment practice

The usable residue is smaller than the headline and firmer than the headline deserves.

Naming what is to be learned, in the lesson, in language students recognise, is associated with the largest assessment-side effect in a 152,000-student model — and it is cheap, checkable, and unaffected by whether students are using generative tools. It is also, on the item wording, substantially about structure and explicitness rather than about published rubrics, which matters when the temptation is to write criteria documents rather than change what happens in the first four minutes of a lesson.

Adjusting instruction in response to what assessment shows is the second-largest, and it is the behaviour that most obviously cannot be delegated to a tool. A department that generates excellent feedback and teaches the same sequence regardless has bought the cheap half of formative assessment.

The evenness of feedback is worth watching precisely because it has never been visible. Few schools have ever had a number for how unequally feedback is distributed inside their own building, and this study suggests — weakly, correlationally, at −0.064 SD — that it is the dimension that carries the signal. It is also the one dimension that AI changes fast and in a direction the model likes. That is a monitoring question, not a policy question, and it is answerable with a five-item student survey rather than a platform.

And using assessment data to evaluate people is associated with lower reading scores (−0.062 SD) while using it for learning is associated with nothing at all. Both of those findings are small. Only one of them will ever be quoted in a leadership meeting, and it is the wrong one, because the null on assessment-for-learning policy is the finding that should discipline expectations about what a policy document can achieve. Policy explained one percent of the variance. Classroom practice explained two. Schoolmates' socio-economic status explained more than both together, several times over.

The sentence worth carrying is not "clearer goals, not more feedback." It is: **the amount of feedback was never the variable; the paper's own table says so, and its abstract says otherwise.**

## A note on sources

The article is gold open access under CC-BY. All coefficients, standard errors, summary statistics, factor loadings and questionnaire items quoted above were read from the full text and from Tables 1–4 and Appendix Tables A1–A3 of the published version as it stood on 29 July 2026; the standardised conversions in section 4 are derived arithmetic from Tables 3 and 4, not figures reported by the authors. The 0.158 standard-deviation figure appears in the university release and nowhere in the article, and could not be reproduced from the published tables — the paper notes that "ancillary regressions and statistical tests are available upon request", which may be where it comes from. Whether the journal has since issued a correction for the sample-size discrepancy, the duplicated appendix loadings or the out-of-range summary row was not established.
