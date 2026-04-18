# Youtube

YouTube APIs provide programmatic access to YouTube data including videos, playlists, channels, user interactions, live streaming, analytics, captions, and embedded player controls.

## APIs

| API | Description |
|---|---|
| Youtube Activities API | Manages YouTube user activities, including videos liked, channels subscribed to, and other user interactions on YouTube. |
| Youtube Channels API | Provides access to YouTube channel data including channel metadata, statistics, and settings. |
| Youtube Comments API | Manages individual comments on YouTube videos and other resources. |
| Youtube Comment Threads API | Provides access to comment threads on YouTube videos and channels. |
| Youtube Playlists API | Manages YouTube playlists including creating, updating, deleting, and listing playlists. |
| Youtube Playlist Items API | Manages individual items within a YouTube playlist. |
| Youtube Search API | Searches across YouTube content including videos, channels, and playlists. |
| Youtube Subscriptions API | Manages YouTube channel subscriptions. |
| Youtube Videos API | Provides access to YouTube video data including metadata, statistics, and content details. |
| Youtube Captions API | Manages caption tracks associated with YouTube videos. |
| Youtube Channel Sections API | Manages sections that a channel has chosen to feature on its channel page. |
| Youtube Channel Banners API | Enables uploading a new banner image to a YouTube channel. |
| Youtube Members API | Provides access to channel membership data. |
| Youtube Memberships Levels API | Provides information about membership pricing tiers. |
| Youtube Thumbnails API | Manages custom video thumbnail images. |
| Youtube Watermarks API | Manages images that display in the corner of a player during playback. |
| Youtube Video Categories API | Provides a list of categories that can be associated with YouTube videos. |
| Youtube Video Abuse Report Reasons API | Retrieves a list of reasons that can be used to report abusive videos. |
| Youtube I18n Languages API | Returns a list of application languages that YouTube supports. |
| Youtube I18n Regions API | Returns a list of content regions that YouTube supports. |
| YouTube Analytics API | Generates custom reports containing YouTube Analytics data. |
| YouTube Reporting API | Retrieves bulk YouTube Analytics data through predefined reports. |
| YouTube Live Streaming API | Enables creating, updating, and managing live events on YouTube. |
| YouTube IFrame Player API | Enables embedding a YouTube video player on websites. |
| YouTube Subscribe Button | Provides an embeddable subscribe button for websites. |
| Youtube Playlist Images API | Manages thumbnail images associated with YouTube playlists. |
| YouTube Content ID API | Enables YouTube content partners to interact with the rights management system. |
| YouTube oEmbed API | Provides an oEmbed-compliant endpoint for embedding YouTube content. |

## Common Properties

| Property | Type |
|---|---|
| Portal | Portal |
| Getting Started | GettingStarted |
| Documentation | Documentation |
| Code Examples | CodeExamples |
| Support | Support |
| SDK | SDK |
| Authentication | Authentication |
| Change Log | ChangeLog |
| Rate Limits | RateLimits |
| GitHub Repository | GitHubRepository |
| GitHub Organization | GitHubOrganization |
| YouTube | YouTube |
| Terms of Service | TermsOfService |
| Branding | Branding |
| Stack Overflow | StackOverflow |
| Sign Up | SignUp |
| API Reference | APIReference |
| Errors | Errors |
| Compliance | Compliance |
| X | X |
| Status Page | StatusPage |
| Blog | Blog |
| Privacy Policy | PrivacyPolicy |

## Features

| Feature | Description |
|---|---|
| Video Management | Upload, update, rate, and delete videos programmatically with full metadata control. |
| Playlist Management | Create, update, and delete playlists and manage playlist items for content organization. |
| Channel Management | Access and update channel metadata, branding, settings, and sections. |
| Search | Search across videos, channels, and playlists with filters for date, location, topic, and more. |
| Comments And Moderation | Create, retrieve, update, and moderate comments and comment threads on videos. |
| Live Streaming | Schedule and manage live broadcasts, streams, live chat, moderators, and super chat events. |
| Analytics And Reporting | Generate custom analytics reports with views, watch time, revenue, and demographic data. |
| Captions | Upload, update, download, and delete caption tracks for video accessibility. |
| Channel Memberships | Access membership data and pricing tiers for channel monetization features. |
| Content ID | Manage digital rights, assets, claims, and policies for intellectual property protection. |
| Embedded Players | Embed YouTube players on websites with full JavaScript playback control. |
| Internationalization | Retrieve supported languages and regions for localized content and UI. |
| OAuth 2.0 Authentication | Secure API access with OAuth 2.0 for user-authorized operations. |
| Quota Management | Monitor and manage API quota usage with per-operation cost tracking. |

## Use Cases

| Use Case | Description |
|---|---|
| Video Publishing Platform | Build automated video upload and management workflows for content creators and media companies. |
| Social Media Dashboard | Aggregate YouTube analytics with other social platforms for unified performance monitoring. |
| Content Moderation | Automate comment moderation and abuse reporting for community management at scale. |
| Live Event Management | Schedule and manage live streaming events with real-time chat and audience interaction. |
| Education Platform | Organize educational video content into playlists with searchable course catalogs. |
| Digital Rights Management | Track and manage content ownership, claims, and monetization policies using Content ID. |
| Video Search Application | Build custom video search experiences with filters for topics, dates, and regions. |
| Analytics Dashboard | Create custom reporting dashboards with channel and video performance metrics. |
| Accessibility Tools | Manage captions and translations to improve video accessibility across languages. |
| Embedded Video Experience | Create branded video experiences with customized embedded players on external websites. |

## Integrations

| Integration | Description |
|---|---|
| Google Cloud Platform | Integrates with GCP for authentication, hosting, and infrastructure services. |
| Google Analytics | Combine YouTube Analytics data with Google Analytics for comprehensive web and video metrics. |
| Google Ads | Connect YouTube content with Google Ads for video advertising campaigns. |
| Firebase | Use Firebase with YouTube APIs for mobile app development with video features. |
| Google Workspace | Embed YouTube videos in Google Docs, Slides, and Sites for collaborative content. |

## Artifacts

| Type | Count | Directory |
|---|---|---|
| OpenAPI | 4 | [openapi/](openapi/) |
| JSON Schema | 63 | [json-schema/](json-schema/) |
| JSON Structure | 61 | [json-structure/](json-structure/) |
| JSON-LD | 5 | [json-ld/](json-ld/) |
| Examples | 61 | [examples/](examples/) |

## Capabilities

4 shared per-API definitions and 4 workflow-oriented capability compositions.

| Capability | Description | Tools |
|---|---|---|
| [Content Management](capabilities/content-management.yaml) | Video lifecycle management including uploading, playlists, captions, and organization. | 15 |
| [Community Engagement](capabilities/community-engagement.yaml) | Comment moderation, subscriptions, and channel management. | 12 |
| [Live Streaming](capabilities/live-streaming.yaml) | Live broadcast scheduling, stream management, and live chat. | 14 |
| [Analytics And Reporting](capabilities/analytics-and-reporting.yaml) | Real-time analytics queries and bulk report scheduling. | 14 |

### Shared Definitions

| API | File |
|---|---|
| YouTube Data API | [shared/data-api.yaml](capabilities/shared/data-api.yaml) |
| YouTube Analytics API | [shared/analytics.yaml](capabilities/shared/analytics.yaml) |
| YouTube Live Streaming API | [shared/live-streaming.yaml](capabilities/shared/live-streaming.yaml) |
| YouTube Reporting API | [shared/reporting.yaml](capabilities/shared/reporting.yaml) |

## Vocabulary

| File | Resources | Actions | Workflows | Personas |
|---|---|---|---|---|
| [youtube-vocabulary.yaml](vocabulary/youtube-vocabulary.yaml) | 21 | 64 | 4 | 8 |

## Rules

| File | Description |
|---|---|
| [youtube-spectral-rules.yml](rules/youtube-spectral-rules.yml) | Spectral ruleset enforcing YouTube API conventions including camelCase paths, PascalCase tags, OAuth2 security, and Microcks compatibility. |

## Maintainers

- **Kin Lane** - [apievangelist.com](https://apievangelist.com) - kin@apievangelist.com
