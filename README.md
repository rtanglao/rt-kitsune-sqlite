# rt-kitsune-sqlite
sqlite of kitsune questions

# first try with april 2020 questions

* 1\. get the questions

```bash
curl https://raw.githubusercontent.com/rtanglao/rt-kits-api2/master/2020BYMONTH/sorted-all-desktop-en-us-2020-04-01-2020-04-30-firefox-creator-answers-desktop-all-locales.csv\
 > april2020-ff-desktop-aaq-questions.csv
```

* 2\. <del>use a text editor and change ' -0800' to '-0800' (remove space)</del> - actually you don't need to do this, just add " %Z" in step 3
* 3\. generate the database
```bash
csvs-to-sqlite -dt created -df "%Y-%m-%d %H:%M:%S %Z" april2020-ff-desktop-aaq-questions.csv april2020-ff-desktop-aaq-questions.db
```
* 4\. do a sample query

```sql
select * from "april2020-ff-desktop-aaq-questions" 
where datetime(created) < datetime('2020-04-02T00:00:01-00:00');

```

