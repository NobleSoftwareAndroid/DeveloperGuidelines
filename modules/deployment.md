# Deployment

## Purpose

This standard operating procedure aims to ensure consistency in the app publishing process. It provides a clear and
standardized set of instructions that everyone involved in the process can follow, regardless of their level of
experience or expertise. This helps maintain a consistent level of quality across different app releases. Overall, an
SOP for Android app publishing provides structure, consistency, and efficiency to the process, while ensuring compliance
with guidelines and delivering a high-quality app to the Google Play Store. It helps optimize the workflow, reduce
errors, and improve the overall user experience of your app.

## Scope

This document describes the steps the Visi Prima Nusantara Android developer team needs to take whenever the team wants to
publish the app to the Play Store.

Responsibility
It’s the responsibility of the Visi Prima Nusantara developer team to ensure that all the below steps are adhered to,
and take care of all steps before publishing the app to the Play Store.

## Procedure

1. All Developer commit his code on Development branch after QA testing we will move in production and UAT.

2. Make sure the application is fully developed, tested by QA, and ready for release, then build the APK/APP Bundle.
   Check all features and updates.
   Make sure to increase the database version if there are any changes regarding the database.


3. Write a Documentation for release
   Note the latest database version that will be in the current release.
   Note the release description in English and Bahasa.
4. Go to Google Play Console, create a new release for Open Testing and don’t forget to set roll-out percentage to
   100% .

5. Inform to the team after the application is released to Open Testing then we can do testing with the QA team and
   other members in the company.

6. Once it’s confirmed ready for release (after checked, bug free, and other trouble), we can go to the next step.
   Otherwise, if it’s confirmed not ready for release, it should go back to the first step.

7. Go to Google Play Console, create a new release for Production and don’t forget to set roll-out percentage to 100%.

8. Once the application is live on Google Play Store, don't forget to fill the Android Version History on Django Admin.

9. Note all the release updates and information into this spreadsheet.

For more detail, please check out our docs here : [Android Application Publishing Standard Operating Procedure (SOP)](https://docs.google.com/document/d/1pq2ASI3DCtMUZEFs34s0foWHDyzXPlscU3GhxG3vfu4/edit?usp=sharing)
