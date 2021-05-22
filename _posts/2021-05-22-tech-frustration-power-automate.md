---
layout: post
title:  "This week in tech frustration: Microsoft Power Automate"
tags: technology
excerpt: "There should be an easy way to create Team Meetings from an Excel Spreadsheet? Sure, if you're prepared for lots of trial and error."
---
So, this week I've had to create several meetings for students in Teams, and I already had an Excel Spreadsheet with a list.
My technology-minded brain immediately thought "That's a lot of work, why not try to automate that?".

I remembered we had a tool called **Flow** with an icon that expresses the idea of blocks being connected, so I went to our Office 365 portal and... (**Frustration #1**) I couldn't find it.

So then I went to my favourite search engine, and the first result was **flow.microsoft.com** which, despite the URL, is now called **Power Automate** and has a whole new icon.

After exploring a bit, I decided to create a new flow, and I found an Excel connector, and a Teams connector, so I thought that would be very straightforward.

The Excel trigger (aptly named **For a selected row**) lets you choose a file that is already online, by selecting the Location ("OneDrive"), then the Document Library ("OneDrive" too, not sure what's the difference), the file itself, and the table within the file.

Here (**Frustration #2**), I couldn't choose a table, there were "No items".
That's because I did what most Excel users that I know of do, I just put data in a worksheet without **defining** a part of the worksheet as being a table.
The easiest way to do so is to choose "Format as table" in the Home Ribbon.

OK, things are better now. Let's move to the **Create a Teams Meeting** connector.
You start by choosing a Calendar ID (the options are "Calendar", "Birthdays" and "United States Holidays", which is weird because I've never had access to the US holidays anywhere, Outlook only shows me the Dutch ones).
The next mandatory field is the Meeting subject and here the really nice thing is that I can pick the name of a column from my spreadsheet.

Or maybe I can use an expression, but there is absolutely no information on how to use dynamic content from my Excel spreadsheet.
I don't need that for now, but another detour via a search engine tells me I may have to write `triggerBody()?['columnName']` - don't trust me, I haven't tried it yet.

Time zone is mandatory - I'm not sure whether to use "Central Europe Standard Time" or "Central European Standard Time" though.
Start time is mandatory - that's fine.
End time is mandatory - Oh, I don't have this column, I only have the duration, but I can go back to my Spreadsheet and add an "End Time" column based on a simple formula which is `=[@StartTime]+[@Duration]`

I'm coming back from Excel, so I'll refresh the browser to update and add the other fields, which are the attendees.
Now I can save my first flow.

There is a nice "Test" button at the top right, so I'll try it.

Nope. **Frustration #3** "This flow cannot be triggered for testing".
I click around the Power Automate interface and **I cannot find any way to run my script**!

Let's go back to the search engine.
It turns out that a trigger named "For a selected row" can only be run in Excel, by selecting the row, going to the "Data" ribbon and clicking on "Flow".

Only... **Frustration #4**, there is no "Flow" button!

Back to search engine. I need to install an Excel add-in first.

Add-in installed. Flow button appears. But my script isn't there. **Frustration #5**. So I'll create a new one. By the time I'm done, the old flow that I had created and couldn't see before has appeared.

OK, now I'm ready, I can select my row (which I do by clicking on the row number). But wait (**Frustration #6**), why is the "Run" button greyed out?

Well apparently, I'm using the wrong way of selecting a row. You have to select any cells in the table, but make sure that you're not selecting anything outside the table.

Ok, the button is blue, I click... And a few seconds later (**Frustration #7**), it fails.

What happens is that the **Teams** connector won't recognize an **Excel** date field as a date.
Which is ironic, since Excel is famous for transforming absolutely anything into a date to the point that [biologists have had to rename genes to avoid errors](https://www.theverge.com/2020/8/6/21355674/human-genes-rename-microsoft-excel-misreading-dates).

No, Teams wants a text field, in the ISO 8601 standard format "2021-05-22T17:43:00" (no time zone, please, that's another field).

So I went to Excel and added two more columns, so that I could translate the date into the right format.
Excel doesn't have built-in support for ISO 8601, so you have to write it in full.
According to search engine results, the right formula is something like `=TEXT([@StartTime],"yyyy-mm-ddThh:MM:ss")`.

Do you think it worked? NO!!! **Frustration #8**, the result of my formula shows **"yyyy-05-22Thh:43:00"**.

That's because Excel expects a date format in Dutch, not in English.
Even though the whole user interface of Excel and Windows on my laptop are in English.
Because it's a different setting within the regional settings of the laptop.
If I want to have euros, a 24 hour clock and commas as decimal separator, I also have to have Excel use "jjjj" as year formats.

So now I've changed to formula to `=TEXT([@StartTime];"jjjj-mm-ddTuu:MM:ss")` (yes, the separator for arguments in a formula is also different, it's a semi-colon in English-speaking Dutch-version Excel).

And now it works!!!

But why is it so frustrating?
Why can't Microsoft provide more support in their own apps without require me to Google things?
Why can't two programs from the same vendor work out a common way of processing dates?

Why can't a company with a massive R&D department, a company that employs some of the best human-computer interaction researchers in the world, just make an effort to **design** things correctly?
