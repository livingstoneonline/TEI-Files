# [Addressee page issue](https://github.com/livingstoneonline/livingstoneonline/issues/210)

> state: **closed** opened by: **awisnicki** on: **2017-9-14**

The addressee page is missing the top section of the page with carousel, overview, etc.

http://livingstonestage.lib.umd.edu/browse/addressee

### Comments

---
> from: [**awisnicki**](https://github.com/livingstoneonline/livingstoneonline/issues/210#issuecomment-329559350) on: **2017-9-14**

Similar issue for this page: http://livingstonestage.lib.umd.edu/behind-the-scenes/acknowledgments
---
> from: [**nigelgbanks**](https://github.com/livingstoneonline/livingstoneonline/issues/210#issuecomment-329849549) on: **2017-9-15**

The outbound link got reset in the migration it&#x27;s now been changed to:

http://livingstonestage.lib.umd.edu/in-his-own-words/addressee

So http://livingstonestage.lib.umd.edu/browse/addressee is no longer linked to (page is auto-generated by Drupal, but we have no links to it).

&gt; Similar issue for this page: http://livingstonestage.lib.umd.edu/behind-the-scenes/acknowledgments

I can&#x27;t seem to reproduce this issue.
---
> from: [**nigelgbanks**](https://github.com/livingstoneonline/livingstoneonline/issues/210#issuecomment-329850473) on: **2017-9-15**

Though there is a seperate issue with the &lt;hr&gt; element being hidden (looks like more manual changing of the content will be required). 
---
> from: [**awisnicki**](https://github.com/livingstoneonline/livingstoneonline/issues/210#issuecomment-329867497) on: **2017-9-15**

Thanks for sorting Addressee. Re: the &lt;hr/&gt; on Acknowledgments and, indeed, many other pages, note that we always add that at the top of Main Text section. Perhaps, the path of least resistance is to leave that as is and simply remove it from the bottom of the overview section? Previously it did not appear at the bottom of the overview, hence why we added it manually to every page. In any case, feel free to resolve this however, you think is easiest/best.
---
> from: [**nigelgbanks**](https://github.com/livingstoneonline/livingstoneonline/issues/210#issuecomment-329868279) on: **2017-9-15**

Ya I was hiding it before since the overview section had two matching hr elements, but now I&#x27;ll just remove them all and add a default one for when the overview is empty.
---
> from: [**awisnicki**](https://github.com/livingstoneonline/livingstoneonline/issues/210#issuecomment-329870236) on: **2017-9-15**

OK, sounds good. I&#x27;m going to close this and continue in #214 since this is related to that.
---
> from: [**awisnicki**](https://github.com/livingstoneonline/livingstoneonline/issues/210#issuecomment-331215062) on: **2017-9-21**

I&#x27;m going to reopen this issue as I see at least one instance (on the site guide page) of the link pointing to the wrong URL: http://livingstonestage.lib.umd.edu/browse/addressee rather than the correct one. Perhaps do a batch replace in case there are other such instances also.
---
> from: [**nigelgbanks**](https://github.com/livingstoneonline/livingstoneonline/issues/210#issuecomment-336630484) on: **2017-10-14**

Should be sorted now.
---
> from: [**awisnicki**](https://github.com/livingstoneonline/livingstoneonline/issues/210#issuecomment-336644766) on: **2017-10-14**

OK, thank you. If any other instances come up after migration to prod, I&#x27;ll take them of them.