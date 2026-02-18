\documentclass[11pt,a4paper]{article}

\usepackage{graphicx}
\usepackage{hyperref}
\usepackage{amsmath}
\usepackage{booktabs}
\usepackage{geometry}
\usepackage{titlesec}
\usepackage{xcolor}

\geometry{margin=1in}

\title{\textbf{Air Quality-Driven Early Warning Health Risk Prediction System}}
\author{Alka}
\date{}

\begin{document}

\maketitle

\begin{center}
\textit{A Machine Learning Based Environmental Health Risk Prediction Framework}
\end{center}

\section*{Abstract}

This project presents a machine learning based system that predicts environmental health risk levels from air pollution exposure patterns. Unlike conventional air quality systems that only report present pollution levels, this model analyzes historical pollutant exposure and classifies whether a day is \textbf{High Risk} or \textbf{Normal Risk}. The system provides an early warning to support preventive awareness and health precautions.

\section{Problem Statement}

Most air quality monitoring systems report only current pollution levels.  
They do not determine whether accumulated exposure over recent days is dangerous.

This project predicts health risk based on \textbf{cumulative exposure patterns}, enabling individuals to take preventive measures before serious health impact occurs.

\section{Objectives}

\begin{itemize}
\item Analyze historical air quality data
\item Identify pollution exposure patterns
\item Classify high-risk environmental days
\item Provide a simple early warning interface
\end{itemize}

\section{Dataset}

\textbf{Dataset:} Air Quality Data in India (2015–2020) \\
\textbf{City Used:} Delhi \\
\textbf{Source:} CPCB – Government of India (Kaggle) \\
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

These pollutants are strongly linked to respiratory and cardiovascular health risks.

\section{Methodology}

\subsection{Data Preprocessing}

\begin{itemize}
\item Filtered Delhi city data
\item Converted Date column to datetime
\item Sorted chronologically
\item Missing values handled using time-based interpolation
\end{itemize}

\subsection{Feature Engineering}

To capture exposure rather than single-day values:

\subsubsection*{Lag Features}
\begin{itemize}
\item Previous 1-day level
\item Previous 3-day level
\item Previous 7-day level
\end{itemize}

\subsubsection*{Rolling Exposure}
\begin{itemize}
\item 3-day moving average
\item 7-day moving average
\end{itemize}

\subsection{Target Variable}

A day is labeled \textbf{High Risk} if:

\[
PM2.5_{3-day\ average} > Threshold
\]

This reflects cumulative exposure impact rather than instant pollution spikes.

\section{Model Training}

The problem is formulated as a \textbf{Binary Classification} task.

\subsection*{Models Trained}
\begin{itemize}
\item Logistic Regression
\item Random Forest
\item XGBoost
\end{itemize}

A time-based train-test split was used to avoid data leakage.

\section{Evaluation Strategy}

Priority was given to \textbf{Recall} to avoid missing dangerous days.

\subsection*{Metrics Used}

\begin{itemize}
\item Accuracy
\item Precision
\item Recall
\item F1 Score
\item False Negatives
\end{itemize}

\textbf{Random Forest} was selected as the final model.

\section{Deployment}

A Gradio web interface allows users to input pollutant values and receive:

\begin{itemize}
\item High Risk / Normal Risk prediction
\item Confidence score
\item Health advisory
\end{itemize}

\section{How to Run}

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

\section{Limitations}

\begin{itemize}
\item Trained on single city (Delhi)
\item Not connected to real-time sensors
\item Not a medical diagnosis system
\item Based only on environmental exposure
\end{itemize}

\section{Future Work}

\begin{itemize}
\item Real-time pollution API integration
\item Next-day forecasting using time-series models
\item Personalized alerts
\item Smart city integration
\end{itemize}

\section{References}

Central Pollution Control Board (CPCB), Government of India \\
Air Quality Data in India (2015–2020) \\
\url{https://www.kaggle.com/datasets/rohanrao/air-quality-data-in-india}

\vspace{1cm}

\begin{center}
\textbf{Author: Alka}
\end{center}

\end{document}
