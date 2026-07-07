# Placement Preparation Dashboard - Database Design

## Overview

The Placement Preparation Dashboard is a centralized platform that helps
students monitor their placement preparation journey from a single
dashboard. Students register once by providing their coding profile
links. The system automatically retrieves progress and displays coding
statistics, analytics, company readiness, and placement insights.

------------------------------------------------------------------------

# Database Collections

## 1. Users

**Purpose:** Stores login credentials and personal information.

  Field          Type       Description
  -------------- ---------- --------------------
  userId         ObjectId   Unique user ID
  name           String     Student Name
  email          String     Email Address
  password       String     Encrypted Password
  college        String     College Name
  branch         String     Branch
  year           Number     Current Year
  cgpa           Number     CGPA
  phone          String     Phone Number
  profileImage   String     Profile Picture
  role           String     Student/Admin
  createdAt      Date       Registration Date
  
Powered Features:

Student Registration
Login & Authentication
User Profile
Role-based Access

Data Usage:
The data is collected during registration and used for user authentication, profile management, and identifying the student across all other collections using userId.
------------------------------------------------------------------------

## 2. CodingProfiles

**Purpose:** Stores coding platform profile links.

  Field              Type
  ------------------ ----------
  profileId          ObjectId
  userId             ObjectId
  leetcodeUrl        String
  hackerrankUrl      String
  codechefUrl        String
  codeforcesUrl      String
  geeksforgeeksUrl   String
  githubUrl          String
  linkedinUrl        String
  resumeUrl          String

Powered Features:

Coding Profile Integration
Automatic Progress Fetching

Data Usage:
Students provide their coding profile URLs during registration. These links are used by the backend to fetch coding statistics from different coding platforms whenever the dashboard is refreshed.
------------------------------------------------------------------------

## 3. CodingStats

**Purpose:** Stores coding statistics fetched automatically.

  Field            Type
  ---------------- ----------
  statId           ObjectId
  userId           ObjectId
  platform         String
  totalSolved      Number
  todaySolved      Number
  easySolved       Number
  mediumSolved     Number
  hardSolved       Number
  contestRating    Number
  streak           Number
  acceptanceRate   Number
  lastUpdated      Date

 Powered Features:

Coding Dashboard
Progress Analytics
Daily Coding Summary

Data Usage:
Stores the latest coding statistics such as solved problems, ratings, streaks, and acceptance rates. The dashboard uses this data to display coding progress and performance.

--------------------------------------------------------------------------

## 4. DailyActivity

**Purpose:** Stores daily coding activity.

  Field            Type
  ---------------- ----------
  activityId       ObjectId
  userId           ObjectId
  date             Date
  platform         String
  problemsSolved   Number
  hoursStudied     Number

Powered Features:

Daily Progress
Weekly Analytics
Monthly Reports
Consistency Tracking

Data Usage:
Stores the number of problems solved and study hours each day. This data is used to generate graphs and track consistency over time.
------------------------------------------------------------------------

## 5. Companies

**Purpose:** Stores company information.

  Field            Type
  ---------------- ----------
  companyId        ObjectId
  companyName      String
  package          Number
  location         String
  cgpaRequired     Number
  skillsRequired   Array
  deadline         Date

Purpose: Stores company information and eligibility criteria.

Powered Features:

Company Dashboard
Eligibility Checker

Data Usage:
Contains company details such as package, required CGPA, skills, and deadlines. Students can view companies they are eligible to apply for.
------------------------------------------------------------------------

## 6. StudentCompanyProgress

**Purpose:** Tracks company preparation and application status.

  Field                Type
  -------------------- ----------
  progressId           ObjectId
  userId               ObjectId
  companyId            ObjectId
  status               String
  aptitudeCompleted    Boolean
  codingCompleted      Boolean
  interviewCompleted   Boolean
  appliedDate          Date

Status: - Preparing - Applied - Online Assessment Cleared - Technical
Interview - HR Interview - Selected - Rejected

Powered Features:

Company-wise Preparation
Application Tracking
Placement Status

Data Usage:
Stores each student's progress for different companies, including preparation status and interview stages.

------------------------------------------------------------------------

## 7. Goals

**Purpose:** Stores personal coding goals.

  Field       Type
  ----------- ----------
  goalId      ObjectId
  userId      ObjectId
  goalType    String
  target      Number
  completed   Number
  deadline    Date

Powered Features:

Goal Tracker
Progress Monitoring

Data Usage:
Stores coding and study goals created by students and tracks their completion percentage.
------------------------------------------------------------------------

# Entity Relationship


Users
│
├── CodingProfiles (1:1)
├── CodingStats (1:Many)
├── DailyActivity (1:Many)
├── Goals (1:Many)
└── StudentCompanyProgress (1:Many)
              │
              ▼
          Companies

