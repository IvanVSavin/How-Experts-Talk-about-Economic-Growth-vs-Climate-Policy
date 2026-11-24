# How-Experts-Talk-about-Economic-Growth-vs-Climate-Policy
How Experts Talk about Economic Growth vs Climate Policy

This repository contains the code behind the manuscript "How Experts Talk about Economic Growth vs Climate Policy: A Linguistic Analysis". With it, you can reproduce every figure, table and number reported in the paper and its appendices.

What the paper is about

Should climate policy aim for green growth, ignore growth, or accept that the economy must stop growing or even shrink? Experts disagree, and earlier surveys have shown how far apart their positions are. Our paper asks a different question: how do experts reason about this debate, and what lies behind their disagreement?

Between November 2025 and February 2026 we surveyed researchers who had published in six leading journals of environmental and ecological economics. Besides closed-ended questions, the survey asked one open question: what does the long-standing debate about economic growth versus the environment imply for the design of climate policy? We analyse the 776 answers to this question in two ways:

A structural topic model shows which themes respondents write about, and how these themes vary with their position on growth and their background.
AI-assisted qualitative coding records, for every answer, which growth positions it supports or criticises, which kinds of arguments it uses, what it says about the debate itself and which policy instruments it argues for or against. A large language model does the coding, following fixed written instructions, and backs every judgement with a verbatim quote from the answer.

In short, the paper finds the following:

Experts holding different positions on growth raise different themes and arguments. Supporters of degrowth and a steady-state economy stress ecological limits and values, while their critics stress political feasibility and the benefits of growth.
Environmental and ecological economists differ even when they hold the same position.
More than half of the respondents comment on the debate itself, often seeing it as an obstacle to climate action.
Across positions, experts favour direct regulation, social policies and beyond-GDP indicators, whereas carbon pricing divides them.
What is in this repository

All results come from one R Markdown file, analysis/reproduce_results.Rmd. Section 8 of this file follows the order of the paper: each figure and table has its own heading, and its code chunk is named after it (for example, paper-fig3 produces Figure 3 and paper-tableA2 produces Table A2). Sections 1–7 document how the data were prepared, how the topic model was chosen and how the AI-assisted coding was checked.

The other files are:

run_all.R	Runs everything in one go
install_packages.R	Installs the R packages needed
prompts/	The instructions given to the language model (Appendix B of the paper) and the rules for selecting illustrative quotes
data/README.md	The input files you need, with checksums
expected_output/	The figures of the paper and a list of every number in the text, exactly as produced for the manuscript
R_session_info.txt	The versions of R and of the packages we used

The data

The folder data/ holds everything the analysis needs: the survey responses, the cleaned and translated data, the saved topic model, the AI-assisted coding and the authors' review of it. Before publishing, we removed what could identify respondents directly. The survey export no longer contains contact IDs, IP addresses, browser information or the location derived from the IP address. One email address and three passages in which respondents described their own role, publication or place of residence were replaced by a note in square brackets. The reviewers of the coding are numbered rather than named. data/README.md explains these changes in detail and lists every file with its checksum.
None of these changes affects the results: with the published data, the code reproduces every figure, table and number of the article.

How to run it
Install R (version 4.3 or later) and then the packages: Rscript install_packages.R. Knitting to Word also needs pandoc, which comes with RStudio.
Put the input files in the folder data/.
From the main folder of the repository, run Rscript run_all.R. On Linux or macOS, use a UTF-8 locale, for example LANG=C.UTF-8 Rscript run_all.R.

The whole run takes a few minutes, because the topic model is loaded rather than estimated again.

What you get

The results are written to the folder output/:

reproduce_results.docx, a full report with every analysis, the figures and tables of the paper with their captions, and the values behind each figure;
paper_figures/, with every figure of the paper as a PNG file (300 dpi), and paper_numbers.csv, with every number cited in the text.

At the end, run_all.R compares your numbers with those in expected_output/ and tells you how many differ. With the original data, none do. The last annex of the report also lists every number written in the manuscript next to the value the code computes.

A note on the AI-assisted coding

The coding was done once, with Claude (version claude-opus-5-5), and its results are part of the input data (ai_codes_v3.csv). You therefore do not need access to a language model to reproduce the paper. The report checks that every supporting quote appears word for word in the answer it comes from. It also compares the coding with the authors' own review of 300 randomly drawn answers, in which the reviewers agreed with all codes in 93% of cases (Appendix C of the paper).

If you want to run the coding again, the chunk ai-reproduce in the R Markdown file shows how. It is switched off by default and needs the R package ellmer and an Anthropic API key. A new run may differ slightly from the saved coding.

Questions and citation

If something does not work, or you would like the data, please contact the corresponding author of the article ay isavin@escp.eu. If you use this code, please cite the article; the full reference will be added here once it is published.
