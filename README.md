# 🔧 Services

These are microservices for automating everyday tasks, written in TypeScript/Node.js and deployed to [ZEIT](https://zeit.co).

## ⭐ Endpoints

### `/wikipedia-summary`

Returns the introductory text for a search term. 

| Query param | Description               | Example     |
| ----------- | ------------------------- | ----------- |
| `q`         | Search query              | Oswald Labs |
| `limit`     | Max length of summary     | 300         |
| `min`       | Minimum length of summary | 8           |
| `cacheAge`  | Seconds to cache for      | 86400       |

### `/github-contributors`

Returns an SVG image with profile pictures of contributors of a repository on GitHub. 

| Query param    | Description                        | Example            |
| -------------- | ---------------------------------- | ------------------ |
| `repo`         | GitHub repository path             | elninotech/uppload |
| `width`        | Profile picture width in pixels    | 85                 |
| `itemsPerLine` | Number of pictures per line        | 8                  |
| `padding`      | Padding between pictures in pixels | 5                  |
| `cacheAge`     | Seconds to cache for               | 86400              |

### `/github-members`

Returns an SVG image with profile pictures of members of a repository on GitHub.

| Query param    | Description                        | Example    |
| -------------- | ---------------------------------- | ---------- |
| `org`          | GitHub organization name           | elninotech |
| `width`        | Profile picture width in pixels    | 85         |
| `itemsPerLine` | Number of pictures per line        | 8          |
| `padding`      | Padding between pictures in pixels | 5          |
| `cacheAge`     | Seconds to cache for               | 86400      |


### `/github-files`

Returns a [Shields.io schema](https://shields.io/endpoint) for a badge with the number of files in a GitHub repository's directory.

| Query param            | Description                   | Example            |
| ---------------------- | ----------------------------- | ------------------ |
| `repo`                 | GitHub repository path        | elninotech/uppload |
| `path`                 | Directory path                | src/i18n           |
| `add`<sup>1</sup>      | Add to number of files        | 0                  |
| `subtract`<sup>1</sup> | Subtract from number of files | 1                  |
| `label`                | Shield label                  | i18n               |
| `message`<sup>2</sup>  | Shield message                | $1$ language$S$    |
| `color`                | Shield color                  | blueviolet         |
| `cacheAge`             | Seconds to cache for          | 3600               |

- <sup>1</sup> Add and subtract numbers can be used, for example, to subtract the index.html file and return the number of content files
- <sup>2</sup> Special variables $1$ and $S$ are replaced with the number of files and pluralized "s" respectively

### Life data endpoints

These endpoints are used as webhooks for a cron job, and fetch data from various web services' APIs and update my [Life Data GitHub repo](https://github.com/AnandChowdhary/life-data).

| Endpoint                | Description                            | File                                                                                                           |
| ----------------------- | -------------------------------------- | -------------------------------------------------------------------------------------------------------------- |
| `/spotify`              | My top artists data from Spotify       | [top-artists.yml](https://github.com/AnandChowdhary/life-data/blob/master/top-artists.yml)                     |
| `/wakatime`             | My programming data from Wakatime      | [development.yml](https://github.com/AnandChowdhary/life-data/blob/master/development.yml)                     |
| `/owntracks`            | My real-time location from OwnTracks   | [location.json](https://github.com/AnandChowdhary/life-data/blob/master/location.json)                         |
| `/yoga`                 | My heart rate from HealthKit           | [heart-rate.yml](https://github.com/AnandChowdhary/life-data/blob/master/heart-rate.yml)                       |
| `/yoga`                 | My step count from HealthKit           | [step-count.yml](https://github.com/AnandChowdhary/life-data/blob/master/step-count.yml)                       |
| `/yoga`                 | My flights climbed from HealthKit      | [flights-climbed.yml](https://github.com/AnandChowdhary/life-data/blob/master/flights-climbed.yml)             |
| `/yoga`                 | My distance from HealthKit             | [distance.yml](https://github.com/AnandChowdhary/life-data/blob/master/distance.yml)                           |
| `/yoga`                 | My active energy from HealthKit        | [active-energy.yml](https://github.com/AnandChowdhary/life-data/blob/master/active-energy.yml)                 |
| `/yoga`                 | My basal energy from HealthKit         | [basal-energy.yml](https://github.com/AnandChowdhary/life-data/blob/master/basal-energy.yml)                   |
| `/instagram-highlights` | My story highlights from Instagram     | [instagram-highlights.json](https://github.com/AnandChowdhary/life-data/blob/master/instagram-highlights.json) |
| `/pocket-casts`         | My podcasts list from Pocket Casts     | [podcasts.yml](https://github.com/AnandChowdhary/life-data/blob/master/podcasts.yml)                           |
| `/pocket-casts`         | My listening history from Pocket Casts | [podcast-history.yml](https://github.com/AnandChowdhary/life-data/blob/master/podcast-history.yml)             |
| `/gmail`                | My email summary from Gmail            | [emails.yml](https://github.com/AnandChowdhary/life-data/blob/master/emails.yml)                               |

## 💻 Development

Several secret keys are required to run these services, particularly my private access tokens for third-party services.

- Locally, they are available in the `.env` file.
- On Now, they come from `now.json` using Now Secrets
- As backup, the are available in this repo in [`secrets.gpg`](./secrets.gpg), using the public key [`public.asc`](./public.asc)

## 📄 License

[MIT](https://github.com/devguy4u/services/blob/master/LICENSE) © [SmilyBull](https://github.com/devguy4u)
