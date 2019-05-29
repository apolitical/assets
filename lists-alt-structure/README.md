## Making a new list

When making a list you have two main options:
1. This is a new iteration on a past list.

> eg. `gender-equality-100` 2020

In this case there is already a `gender-equality-100` folder.
Find that and move on to the next section.

2. This is either a new kind of list or we are changing the naming scheme:

> eg `top-apolitical-employee-100`

For either of these cases there will not be a pre-existing folder, you need to create one.

Try to keep the naming scheme consistent. This will appear in the URL so make it something ready for public consumption and SEO friendly. Our naming convention so far puts the `-100` at the end.

## Adding Status data

Within these folders you should see a selection of files sorted by year.

> e.g 2018.json, 2018-status.json, 2019.json, 2019-status.json

Status files control the holding page and are information _about_ a list. They must have the first part of the file name that matches the data file, then a `-status` before the `.json`.
They should always contain the following information:

- **publicationDate**: A string formatted date specifically in format YYYY-MM-DD HH:MM:SS.NNN+TZ eg: "2019-03-20 13:30:00.000+00"

This is important, this time will tell the frontend application when to stop rendering the holding page and instead start rendering the Live data.

- **listName**: A string that is the human ready title for the page

- **listSlug**: A string that is the relative URL for this page

- **variant**: A string tells you what version of this list this is. Most often a variant is a year (e.g. we have the 2018 and 2019 variants of the gender list)

A valid example would be:
```
{
  "publicationDate": "2019-03-20 13:30:00.000+00",
  "listName": "The World's 100 Most Influential People In Climate Policy",
  "listSlug": "most-influential-climate-100/2018",
  "variant": "2018"
}
```

Adding this will mean that if you visit the `/lists` endpoint with the slug and variant you should be able to see a published list. Eg:
`apolitical.co/lists/most-influential-climate-100/2018`

## Adding a default route

But what if you just go to:
`apolitical.co/lists/most-influential-climate-100/` how do we know which of the lists to render?

You need to add a `default.json` file which very simply has a single value telling us which file to use. eg:

```
{
  "default": "2018"
}
```

The value for default must match the file name exactly (eg. above would match to 2018.json) but can omit the file type.

## Adding list data

List files must be carefully structured. If you are unsure how to start copy across an older one and change the values from that base.

The top level of the data structure contains the following:
- `metaData` - Information required for Meta tags and SEO within the article. Without these twitter cards and open graph links will not render nicely.
- `hero` - Data and images to be used in the banner
- `pre` - An introductory preamble (a paragraph or two) to the list. Stored and rendered as santized HTML.
- `footer` - information that goes at the base of the list, ususally either photo credits, references or methodology info.
- `gallery` - an array of gallery objects, these represent the data for a card
- `galleryOrder` - an array that defines which sections should be rendered in which order.
