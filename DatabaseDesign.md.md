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

