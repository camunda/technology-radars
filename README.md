# Camunda Technology Radars

![radar](https://insights-images.thoughtworks.com/Build20Your20Own20Technology20Radar20Article01_6e6c10a7f14a74a69d7308f3d77af5ce.png)

A collection of data to generate technology radars for various Camunda Engineering Teams.

## Team Radars

The radars can be seen at `https://<team>.radar.camunda.cloud`, for instance:

- [CamBPM](https://cambpm.radar.camunda.cloud)
- [Cawemo](https://cawemo.radar.camunda.cloud)
- [Cloud](https://cloud.radar.camunda.cloud)
- [Infrastructure](https://infra.radar.camunda.cloud)
- [Operate](https://operate.radar.camunda.cloud)
- [Optimize](https://optimize.radar.camunda.cloud)
- [Shared Services](https://shared.radar.camunda.cloud)
- [Zeebe](https://zeebe.radar.camunda.cloud)

If your team is not there, just add a coressponding `<team>.csv` file to this repo and a link to the list above.
The radar will be available at `<team>.radar.camunda.cloud` automagically.

## Why?

- To have a central place to display a technological map for the teams, including both the actively used techonologies and the ones that may become such one day (or not).
- To help the teams to sync on the stacks they're using (imagine you're considering technology X for adoption, and you notice another team already evaluated it - you can learn from their experience!)
- To be shared with the outer world (e.g. in job descriptions), also helping the newcomers with the onboarding process, especially if the radar data is full enough and the item descriptions are elaborate.

## Structure

All technologies are separated into four segments and four adoption circles.

⚠️ We're using an external [service](https://radar.thoughtworks.com) to generate the radar data, and they have a strict limitation on the number of segments and circles. The source data should have **exactly four** segments and four circles, otherwise the radar will not be generated.

## File format

Check out the [infra.csv](infra.csv) for an example.

The columns are:
```csv
name,quadrant,ring,isNew,description
```

- `name` is the name of a technology (e.g. `Java`)
- `quadrant` is one of the four quadrants for the technology (e.g. `Programming Languages`)
- `ring` is one of the four circles (one of `Adopt`, `Trial`, `Assess`, `Hold`)
- `isNew` is a boolean to mark if something has changed with the technology (e.g. it's been moved to another ring). If `TRUE`, is shown as a triangle, otherwise as a circle.
- `description` (optional) is an HTML-format description of a technology which is displayed when you click on it.

### Quadrants

There has to be **exactly four** quadrants in your data.

Quadrants are arbitratry strings. In the visualization, they are ordered counter-clockwise.

### Rings

There has to be **exactly four** rings in your data.


The circles are (in order from inner to outer):
- `Adopt`: actively used in the production
- `Trial`: something being actively evaluated (e.g. you build POCs with it)
- `Assess`: something worth exploring (e.g. you read about it)
- `Hold`: something that will not be tried or introduced any time soon, or something that has been phased out or is in the legacy stage.

## FAQ

### My radar is not generated

Check the number of the unique segments and circles - it should be exactly four of each.

E.g., four segments and three circles would not work. 

### The circles are not ordered the right way

The backing tool is making the circle order based on the order of the first occurencies of values of the list.

For example, this order of entries:
```
Adopt  # first occurence in the list
Adopt
Trial  # first occurence in the list
Assess # first occurence in the list
Assess
Hold   # first occurence in the list
Hold
Trial
```

will be creating a cirlce order of `Adopt`, `Trial`, `Assess`, `Hold`.

If the order is wrong, make sure the data entries are arranged the right way.

### Can I test my CSV file before merging to master?

There's two easy options:

- A. Change the URL of the sheet to point to your CSV file, for instance:
`https://infra.radar.camunda.cloud/?sheetId=<URL-of-your-CSV>`

- B. Go to https://radar.thoughtworks.com and paste the link to the CSV there.
