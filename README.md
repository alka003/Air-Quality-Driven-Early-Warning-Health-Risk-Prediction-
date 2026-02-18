\documentclass[12pt]{article}

\usepackage[margin=1in]{geometry}
\usepackage{hyperref}
\usepackage{titlesec}
\usepackage{enumitem}
\usepackage{verbatim}
\usepackage{xcolor}

\titleformat{\section}{\large\bfseries}{}{0em}{}
\titleformat{\subsection}{\normalsize\bfseries}{}{0em}{}

\setlist[itemize]{noitemsep, topsep=2pt}

\begin{document}

\begin{center}
{\LARGE \textbf{Air Quality-Driven Early Warning Health Risk Prediction System}}
\end{center}

\vspace{0.5cm}

A machine learning–based system that predicts environmental health risk levels from air pollution exposure patterns.

The model analyzes historical pollutant data and classifies whether a day is High Risk or Normal Risk, helping support preventive awareness.

\section*{Problem Statement}

Most air quality systems only report the current pollution level. \\
They do not indicate whether recent exposure patterns are dangerous.

This project predicts health risk from cumulative exposure, enabling people to take precautions before serious impact.

\section*{Objective}

\begin{itemize}
\item Analyze historical air quality data
\item Identify pollution exposure patterns
\item Classify high-risk environmental days
\item Provide a simple early warning interface
\end{itemize}

\section*{Dataset}

Dataset: Air Quality Data in India (2015–2020) \\
City Used: Delhi \\
Source: Kaggle (CPCB – Government of India) \\
\url{https://www.kaggle.com/datasets/rohanrao/air-quality-data-in-india}

\subsection*{Pollutants Used}

\begin{itemize}
\item PM2.5
\item PM10
\item NO$_2$
\item SO$_2$
\item CO
\item O$_3$
\end{itemize}

These pollutants are linked to respiratory and cardiovascular health risks.

\section*{Methodology}

\subsection*{1. Data Preprocessing}

\begin{itemize}
\item Filtered Delhi city data
\item Converted Date column to datetime
\item Sorted chronologically
\item Handled missing values using time-based interpolation
\end{itemize}

\subsection*{2. Feature Engineering}

To capture pollution exposure instead of single-day values:

\textbf{Lag Features}
\begin{itemize}
\item Previous 1, 3, and 7 day pollution levels
\end{itemize}

\textbf{Rolling Exposure}
\begin{itemize}
\item 3-day moving average
\item 7-day moving average
\end{itemize}

\subsection*{3. Target Variable}

A day is labeled High Risk if:

PM2.5 3-day average $>$ threshold

This reflects cumulative exposure impact.

\section*{Model Training}

Problem formulated as Binary Classification

Models trained:

\begin{itemize}
\item Logistic Regression
\item Random Forest
\item XGBoost
\end{itemize}

Time-based train–test split used to avoid data leakage.

\section*{Evaluation Strategy}

Focus was placed on Recall to avoid missing dangerous days.

Metrics used:

\begin{itemize}
\item Accuracy
\item Precision
\item Recall
\item F1 Score
\item False Negatives
\end{itemize}

Random Forest selected as final model.

\section*{Deployment}

A Gradio web interface allows users to input pollutant values and receive:

\begin{itemize}
\item High Risk / Normal Risk prediction
\item Confidence score
\item Health advisory
\end{itemize}

\section*{How to Run}

\subsection*{1. Clone Repository}
\begin{verbatim}
git clone https://github.com/your-username/air-quality-health-risk.git
cd air-quality-health-risk
\end{verbatim}

\subsection*{2. Install Requirements}
\begin{verbatim}
pip install -r requirements.txt
\end{verbatim}

\subsection*{3. Run Application}
\begin{verbatim}
python app.py
\end{verbatim}

\section*{Limitations}

\begin{itemize}
\item Trained on 'single city (Delhi)
\item Not real-time sensor connected
\item Not a medical diagnosis system
\item Based on environmental exposure only
\end{itemize}

\section*{Future Work}

\begin{itemize}
\item Real-time pollution API integration
\item Next-day forecasting using time-series models
\item Personalized alerts
\item Smart city integration
\end{itemize}

\section*{Reference}

Central Pollution Control Board (CPCB), Government of India \\
Air Quality Data in India (2015–2020) \\
\url{https://www.kaggle.com/datasets/rohanrao/air-quality-data-in-india}

\vspace{0.8cm}

\begin{center}
\textbf{Author}

Alka
\end{center}

\end{document}
