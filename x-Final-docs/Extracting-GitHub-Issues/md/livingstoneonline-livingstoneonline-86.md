# [Multiple XSLT Viewer: adjustments](https://github.com/livingstoneonline/livingstoneonline/issues/86)

> state: **closed** opened by: **awisnicki** on: **2016-10-31**

I would like an assortment of tweaks to the theming of this page. See annotated image attached below. Here is the list of what is in the image:

1. Add dropdown for date, so there will be three buttons above each text. (Adding a third button will, I think, also make the buttons look better over the text without borders.)
2. In the date button, list dates in numerical order, but display them as text.
3. Put 1em padding below buttons.
4. Make buttons say &quot;Select text&quot; &quot;Select page&quot; and &quot;Select date&quot; by default.
5. Remove all black borders.
6. Put some white space padding to the right of the vertical scroll bar in the center.
7. Put a right-left scroll bar at the top (there is already one at the bottom).

![screen shot 2016-10-31 at 17 05 28](https://cloud.githubusercontent.com/assets/12518623/19874139/0883c824-9f91-11e6-9249-a50d7f5796f3.png)



### Comments

---
> from: [**nigelgbanks**](https://github.com/livingstoneonline/livingstoneonline/issues/86#issuecomment-257942224) on: **2016-11-2**

&gt; Add dropdown for date, so there will be three buttons above each text. (Adding a third button will, I think, also make the buttons look better over the text without borders.)

I wrongly assumed that the dates would be used in much the same way as page breaks to be targeted (just with different text). In looking at the generated HTML there is no identifiers generated for dates. I can&#x27;t seem to find them in the XSLT&#x27;s either. For example the following.

&#x60;&#x60;&#x60; HTML
&lt;span class&#x3D;&quot;underline &quot;&gt;
    &lt;span class&#x3D;&quot;&quot;&gt;
        &lt;span class&#x3D;&quot;settlement village&quot; title&#x3D;&quot;Bambarre. Also Bambare, Kabambare, and Kabambarre. Village in Maniema, an eastern region in present-day Democratic Republic of the Congo. Livingstone stayed there 21 September-1 November 1869, 19-26 December 1869, and 22 July 1870-16 February 1871, and wrote most of the 1870 Field Diary there.&quot;&gt;Bambarre&lt;/span&gt;
    &lt;/span&gt;, &lt;span class&#x3D;&quot;&quot;&gt;25 &lt;span class&#x3D;&quot;sup doubleunderline &quot;&gt;th&lt;/span&gt; August, 1870 &lt;/span&gt;. 
&lt;/span&gt;
&#x60;&#x60;&#x60;

The date is broken among several elements and has no identifier for which I can link to in the output.

---
> from: [**nigelgbanks**](https://github.com/livingstoneonline/livingstoneonline/issues/86#issuecomment-257942975) on: **2016-11-2**

&gt; Make buttons say &quot;Select text&quot; &quot;Select page&quot; and &quot;Select date&quot; by default.

It doesn&#x27;t really make sense for &quot;Select text&quot; since one is selected automatically by default. I can add it for the others though.

---
> from: [**nigelgbanks**](https://github.com/livingstoneonline/livingstoneonline/issues/86#issuecomment-257946300) on: **2016-11-2**

&gt; Put a right-left scroll bar at the top (there is already one at the bottom).

This isn&#x27;t supported by any browser, I&#x27;ll have to hack something in to achieve this, do you still want me to move forward with it?

---
> from: [**awisnicki**](https://github.com/livingstoneonline/livingstoneonline/issues/86#issuecomment-257955957) on: **2016-11-2**

Re: dates -- that&#x27;s easy to fix with the XSLT. I&#x27;ll get it sorted and let you know. How would you like it outputted in the HTML? The original (TEI) will look like one of the following:

date
date when&#x3D;&quot;1871-01-01&quot;
date from&#x3D;&quot;1871-01-01&quot; to&#x3D;&quot;1871-02-02&quot;

I could make the date a class, so **span class&#x3D;&quot;date&quot;** and I can also spew out the when/from/to date info in that span however you like. As you can see, some dates will be unknown, so I could spew out something in those cases as well, for instance, &quot;unknown&quot;

Re: select text, sounds good for the other two; leave title as is.

Re: top scroll, let&#x27;s see how the panes look once you&#x27;ve reduced the height and we may not need that.

---
> from: [**nigelgbanks**](https://github.com/livingstoneonline/livingstoneonline/issues/86#issuecomment-257980702) on: **2016-11-2**

We can use data fields to do the value and also the label for example.

&#x60;&#x60;&#x60; xml
&lt;span data-date&#x3D;&quot;1871-01-01&quot; data-label&#x3D;&quot;Jan 1st, 1871&quot;&gt;...&lt;/span&gt;
&#x60;&#x60;&#x60;

Then I could sort the dropdown by the &#x60;data-date&#x60; field and display the &#x60;data-label&#x60; field to the user in the select box. 

---
> from: [**awisnicki**](https://github.com/livingstoneonline/livingstoneonline/issues/86#issuecomment-257981617) on: **2016-11-2**

Sounds good. However, note that the TEI only has the data-date, so you&#x27;d have to generate the data label from that. There may be a way to do this through the XSLT conversion, but that&#x27;s definitely outside of my skill level -- though I could investigate if you like.

---
> from: [**awisnicki**](https://github.com/livingstoneonline/livingstoneonline/issues/86#issuecomment-257990414) on: **2016-11-2**

I&#x27;ve set this up for data-date without a hitch, so once you let me know what you&#x27;d like to do re: data-label I can put up the new XSLT.

---
> from: [**nigelgbanks**](https://github.com/livingstoneonline/livingstoneonline/issues/86#issuecomment-257996619) on: **2016-11-2**

For the label, I assumed you&#x27;d be grabbing the text from the content of the tag? If we only have the &#x60;data-date&#x60; info I can just generate ISO dates like Jan 1st, 1871.

---
> from: [**awisnicki**](https://github.com/livingstoneonline/livingstoneonline/issues/86#issuecomment-258012084) on: **2016-11-2**

The TEI **date** tag will only have a numerical value for the date in the **@when** or **@from** or **@to** attributes, e.g. &quot;1871-10-17&quot;. Note that sometimes it will be, YYYY-MM-DD, sometimes YYYY-MM, and sometimes just YYYY. There are also one or two negative dates for BC, e.g. &quot;-600&quot;

I will put each of value in the data-date field on the span, so in some cases you may have two values separated by a space, eg. **span data-date&#x3D;&quot;1871-10-12 1871-10-17&quot;**. 

The Livingstone text that&#x27;s actually coded may not provide everything that we need, eg. &quot;17th&quot;

As a result, the text version that shows up in the dropdown would have to be generated based on the numerical value of the date that I provide in HTML. It sounds like you can do this, so that&#x27;s good news.

So, please put it in this form in the dropdown:

1 Jan. 1871

I&#x27;ll try to update the XSLT a little later today.

---
> from: [**awisnicki**](https://github.com/livingstoneonline/livingstoneonline/issues/86#issuecomment-258116141) on: **2016-11-3**

The XSLT is now updated on the site and on all Github branches. Dates are now **span class&#x3D;&quot;data&quot; data-date&#x3D;&quot;[numerical date here]&quot;**. Note that the data-date may have one or two values, if two separated by a space: &quot;1871-10-12 1871-10-15&quot;. Also in some cases the date is unknown, in which case the value for data-date is &quot;unknown&quot;

The update was a snap btw.

---
> from: [**nigelgbanks**](https://github.com/livingstoneonline/livingstoneonline/issues/86#issuecomment-258127470) on: **2016-11-3**

K I updated the dev branch to have what you put on stage. What is the expected behvaior when we have multiple dates that are the exact same or for multiple Unknowns?

---
> from: [**nigelgbanks**](https://github.com/livingstoneonline/livingstoneonline/issues/86#issuecomment-258135141) on: **2016-11-3**

When there is a date range like &quot;1871-10-12 1871-10-17&quot; I assume you want it to display like: 
&quot;12 Oct. 1871 - 17 Oct. 1871&quot;?

---
> from: [**awisnicki**](https://github.com/livingstoneonline/livingstoneonline/issues/86#issuecomment-258155360) on: **2016-11-3**

&gt; K I updated the dev branch to have what you put on stage. What is the expected behvaior when we have multiple dates that are the exact same or for multiple Unknowns?

Show each as a separate line to click, sequentially as they appear in transcript, so, for instance, if we have 1871-10-10 twice, then it should appear like this in the dropdown:

10 Oct. 1871
10 Oct. 1871

Ideally, if you could do something like the following, that&#x27;d be even better:

10 Oct. 1871 (1)
10 Oct. 1871 (2)

Also, note that in the drop down, I think it would be better if all dates appears in alphanumeric sequence (with unknown at the end) even if the dates are out of sequence in the transcript in some cases.

&gt; When there is a date range like &quot;1871-10-12 1871-10-17&quot; I assume you want it to display like: &quot;12 Oct. 1871 - 17 Oct. 1871&quot;?

Yes, except no space on either side the dash &quot;12 Oct. 1871-17 Oct. 1871&quot;, that&#x27;s good. However, if it turns out that this makes the drop down too long (and so interferes with mobile), then we could just show the two endpoints as separate entities:

12 Oct. 1871
17 Oct. 1871

---
> from: [**nigelgbanks**](https://github.com/livingstoneonline/livingstoneonline/issues/86#issuecomment-258464839) on: **2016-11-4**

Ready for review on stage.

---
> from: [**awisnicki**](https://github.com/livingstoneonline/livingstoneonline/issues/86#issuecomment-258577066) on: **2016-11-4**

I think most everything you did looks great, so thank you for that. 

However, there are some additional adjustments I&#x27;d like:
1. There&#x27;s something off with the date dropdown as the dates that show up in the dropdown are one behind what&#x27;s actually in the transcription. So, for instance, the text has &quot;1827&quot; but the dropdown shows &quot;1826&quot;; the text has &quot;17 Aug 1870&quot; but the dropdown shows &quot;16 August 1870&quot;.
2. Please modify how the dates are shown in the date drop down as follows:
   a. No period after month name, so 1 Mar 1870
   b. Use &quot;Sept&quot; rather than &quot;Sep&quot;.
   c. June and July can be written out in full.
   d. Restore the space around a dash when there are multiple dates &quot;16 Mar 1871 - 17 Mar 1871&quot;
3. Please select the 1870 Field Diary text, then scroll down in the dates until you find &quot;NaN BCE&quot;. This is a bug. The text says &quot;-600&quot; in the data-date so this should come up as 600 BC and be the first item in the dropdown.
4. When someone selects a date and the text scrolls to that date, could we have it show up highlighted in light gray or something like that?
5. Could you increase the height of the panes very slightly?
6. See attached screen shot for a few additional adjustments.

![screen shot 2016-11-04 at 19 00 36](https://cloud.githubusercontent.com/assets/12518623/20026003/f4fd04b6-a2c2-11e6-977d-ef7bcfe97344.png)

---
> from: [**nigelgbanks**](https://github.com/livingstoneonline/livingstoneonline/issues/86#issuecomment-258840037) on: **2016-11-7**

&gt; There&#x27;s something off with the date dropdown as the dates that show up in the dropdown are one behind what&#x27;s actually in the transcription. So, for instance, the text has &quot;1827&quot; but the dropdown shows &quot;1826&quot;; the text has &quot;17 Aug 1870&quot; but the dropdown shows &quot;16 August 1870&quot;.

I can&#x27;t seem to reproduce this one, can you provide a screen cap? Hmm seems like it might be due to the Date parser provided by javascript, it may be interpreting the dates as as UT hence why I wouldn&#x27;t see the date difference. Is it possible you could generate the date values like so:

&#x60;YYYY/MM/DD&#x60; rather than &#x60;YYYY-MM-DD&#x60;

According to the standard that would then be interpreted in local time (to the viewer), rather than based on Universal Time.

---
> from: [**nigelgbanks**](https://github.com/livingstoneonline/livingstoneonline/issues/86#issuecomment-258851445) on: **2016-11-7**

Ah don&#x27;t worry about the conversion to &#x60;/&#x60; I can do that in code.

---
> from: [**awisnicki**](https://github.com/livingstoneonline/livingstoneonline/issues/86#issuecomment-258864309) on: **2016-11-7**

Good to know as this would have been difficult for me to do.

---
> from: [**nigelgbanks**](https://github.com/livingstoneonline/livingstoneonline/issues/86#issuecomment-260077028) on: **2016-11-11**

Ready for review on stage.

---
> from: [**nigelgbanks**](https://github.com/livingstoneonline/livingstoneonline/issues/86#issuecomment-260077236) on: **2016-11-11**

Side note: The date select as it grows the size of it’s largest item (within a max range to keep it from breaking onto the next line). I can force it to be small in all cases regardless of the text content but then some items when selected will have their text cut off. The other issues are handled and deployed to stage.

---
> from: [**awisnicki**](https://github.com/livingstoneonline/livingstoneonline/issues/86#issuecomment-260096885) on: **2016-11-11**

On desktop, this now looks fantastic as is. I&#x27;ll review again on the next pass for mobile, but right now just two small tweaks, please:

1) The dates are not quite in the right order in the dropdowns. Currently you have &quot;year month day (# of times)&quot;, but the order should be &quot;day month year (# of times),&quot; so incorrect: 1870 Aug 24 (2); correct: 24 Aug 1870 (2).

Also for single digit days, please use just the single digit and no leading zero, so incorrect: 04; correct: 4 etc

2) See the screen shot below and note what happens to the critical edition dropdown at this width this is a bug. It shouldn&#x27;t jump below the gray line.
![screen shot 2016-11-11 at 20 37 16](https://cloud.githubusercontent.com/assets/12518623/20235120/51f2de48-a84f-11e6-88bb-3428110c6d3c.png)

---
> from: [**nigelgbanks**](https://github.com/livingstoneonline/livingstoneonline/issues/86#issuecomment-260184754) on: **2016-11-13**

Number 1 is sorted and on stage, I&#x27;m not sure what&#x27;s wrong in number 2?

---
> from: [**awisnicki**](https://github.com/livingstoneonline/livingstoneonline/issues/86#issuecomment-260188749) on: **2016-11-13**

#1 looks perfect!

For #2, see the bit I&#x27;ve circled. The top of this is going under to the gray line above.
![51f2de48-a84f-11e6-88bb-3428110c6d3c](https://cloud.githubusercontent.com/assets/12518623/20246281/8793c4c4-a9ab-11e6-91ac-c7bab05e8d29.png)

---
> from: [**awisnicki**](https://github.com/livingstoneonline/livingstoneonline/issues/86#issuecomment-260188859) on: **2016-11-13**

Also, please explain how I build a Multi-Viewer page from scratch.

---
> from: [**nigelgbanks**](https://github.com/livingstoneonline/livingstoneonline/issues/86#issuecomment-260189022) on: **2016-11-13**

&gt; For #2, see the bit I&#x27;ve circled. The top of this is going under to the gray line above.

Oh that&#x27;s the fixed navigation bar appearing? It&#x27;s fixed to the top of the browser so if you scroll further up or down you&#x27;ll notice the page moves underneath it.

---
> from: [**nigelgbanks**](https://github.com/livingstoneonline/livingstoneonline/issues/86#issuecomment-260189049) on: **2016-11-13**

&gt; Also, please explain how I build a Multi-Viewer page from scratch.

I&#x27;ll do that in another ticket.

---
> from: [**awisnicki**](https://github.com/livingstoneonline/livingstoneonline/issues/86#issuecomment-260208380) on: **2016-11-13**

OK, everything here looks resolved, so I&#x27;m closing this ticket.

