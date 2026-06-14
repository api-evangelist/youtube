# YouTube GraphQL Schema

## Overview

YouTube does not expose a native public GraphQL API. The YouTube Data API v3 is a REST-based API served at `https://www.googleapis.com/youtube/v3`. This GraphQL schema is a community-defined type mapping derived from the official YouTube Data API v3 resource models documented at [https://developers.google.com/youtube/v3/docs/](https://developers.google.com/youtube/v3/docs/).

The schema file (`youtube-schema.graphql`) models the core resource types, sub-resource parts, and query patterns that correspond to the REST endpoints of the YouTube Data API v3, the YouTube Analytics API, the YouTube Reporting API, and the YouTube Live Streaming API.

## Source APIs

| API | Base URL | Reference |
|-----|----------|-----------|
| YouTube Data API v3 | `https://www.googleapis.com/youtube/v3` | https://developers.google.com/youtube/v3/docs/ |
| YouTube Analytics API | `https://youtubeanalytics.googleapis.com/v2` | https://developers.google.com/youtube/analytics |
| YouTube Reporting API | `https://youtubereporting.googleapis.com` | https://developers.google.com/youtube/reporting |
| YouTube Live Streaming API | `https://www.googleapis.com/youtube/v3` | https://developers.google.com/youtube/v3/live/docs |

## GitHub

- Organization: https://github.com/googleapis
- API Samples: https://github.com/youtube/api-samples

## Type Coverage

The schema covers 54 named types organized into the following groups:

### Core Video Types
- `Video` — full video resource
- `VideoSnippet` — title, description, tags, publishedAt, channelId, thumbnails, localized
- `VideoStatistics` — viewCount, likeCount, commentCount, favoriteCount
- `VideoStatus` — privacyStatus, uploadStatus, embeddable, license, publicStatsViewable
- `VideoContentDetails` — duration, dimension, definition, caption, regionRestriction
- `VideoPlayer` — embedHtml, embedHeight, embedWidth
- `VideoTopicDetails` — topicIds, relevantTopicIds, topicCategories
- `VideoSuggestions` — processingErrors, processingWarnings, processingHints, tagSuggestions
- `VideoRecordingDetails` — recordingDate, location
- `VideoLocalizations` — localized title and description map entries
- `VideoRegionRestriction` — allowed and blocked region codes
- `VideoAbuseReport` — videoId, reasonId, secondaryReasonId, comments

### Core Channel Types
- `Channel` — full channel resource
- `ChannelSnippet` — title, description, publishedAt, country, defaultLanguage, thumbnails
- `ChannelStatistics` — viewCount, subscriberCount, videoCount, hiddenSubscriberCount
- `ChannelStatus` — privacyStatus, isLinked, longUploadsStatus, madeForKids
- `ChannelContentDetails` — related playlists (uploads, likes, favorites)
- `ChannelBrandingSettings` — channel branding, watch page, image settings
- `ChannelSection` — section resource with position, type, and content
- `ChannelBanner` — bannerExternalUrl for uploaded channel banner image

### Playlist Types
- `Playlist` — full playlist resource
- `PlaylistSnippet` — title, description, publishedAt, channelId, thumbnails, tags, localized
- `PlaylistStatus` — privacyStatus
- `PlaylistItem` — item within a playlist
- `PlaylistItemSnippet` — playlist item metadata including position and resourceId
- `PlaylistItemContentDetails` — videoId, startAt, endAt, note, videoPublishedAt
- `PlaylistImage` — thumbnail image for a playlist

### Search Types
- `SearchResult` — a single search result resource
- `SearchResultSnippet` — title, description, channelId, publishedAt, thumbnails, liveBroadcastContent
- `SearchResultId` — kind and id (videoId, channelId, or playlistId)

### Comment Types
- `Comment` — a single comment resource
- `CommentSnippet` — authorDisplayName, textDisplay, likeCount, publishedAt, updatedAt, videoId, parentId
- `CommentThread` — top-level comment plus replies
- `CommentThreadSnippet` — videoId, topLevelComment, canReply, totalReplyCount, isPublic
- `CommentThreadReplies` — list of reply Comment resources

### Subscription Types
- `Subscription` — a channel subscription resource
- `SubscriptionSnippet` — publishedAt, title, description, resourceId, channelId, thumbnails
- `SubscriptionContentDetails` — activityType, totalItemCount, newItemCount

### Caption Types
- `Caption` — a caption track resource
- `CaptionSnippet` — videoId, lastUpdated, trackKind, language, name, audioTrackType, status

### Member and Monetization Types
- `Member` — a channel member resource
- `MemberSnippet` — creatorChannelId, memberDetails, membershipsDetails
- `MembershipLevel` — a channel membership pricing tier
- `MembershipLevelSnippet` — creatorChannelId, levelDetails including displayName
- `SuperChatEvent` — a Super Chat or Super Sticker purchase during a live stream
- `SuperChatEventSnippet` — channelId, displayString, messageType, supporterDetails

### Live Streaming Types
- `LiveBroadcast` — a YouTube live broadcast resource
- `LiveBroadcastSnippet` — title, description, channelId, scheduledStartTime, actualStartTime, thumbnails
- `LiveBroadcastStatus` — lifeCycleStatus, privacyStatus, recordingStatus, madeForKids
- `LiveBroadcastContentDetails` — boundStreamId, enableDvr, enableEmbed, enableAutoStart
- `LiveStream` — a video stream ingested by YouTube
- `LiveStreamSnippet` — channelId, title, description, publishedAt
- `LiveStreamStatus` — streamStatus, healthStatus
- `LiveStreamContentDetails` — ingestionInfo (rtmpsIngestionAddress, streamName), resolution, frameRate
- `LiveChatMessage` — a message in a live chat
- `LiveChatMessageSnippet` — type, displayMessage, authorChannelId, publishedAt
- `LiveChatBan` — a ban applied in a live chat
- `LiveChatModerator` — a moderator of a live chat

### Shared / Utility Types
- `Thumbnail` — url, width, height for a single thumbnail size
- `ThumbnailDetails` — default, medium, high, standard, maxres thumbnail variants
- `PageInfo` — totalResults, resultsPerPage for paginated responses
- `ResourceId` — kind, videoId, channelId, playlistId for polymorphic resource references
- `Localization` — title and description in a specific language
- `Tag` — string tag value on a video or playlist
- `I18nLanguage` — a language supported by YouTube (hl, name)
- `I18nRegion` — a content region supported by YouTube (regionCode, name)
- `VideoCategory` — a category assignable to YouTube videos
- `ActivityResource` — a user activity event (like, favorite, subscription, upload, recommendation)

## Query Patterns

The root `Query` type maps to the primary list and get operations of the YouTube Data API v3:

- `video(id: ID!, part: [String!])` → `Video`
- `videos(ids: [ID!], chart: String, myRating: String, part: [String!], pageToken: String, maxResults: Int)` → `VideoListResponse`
- `channel(id: ID!, part: [String!])` → `Channel`
- `channels(ids: [ID!], mine: Boolean, part: [String!], pageToken: String, maxResults: Int)` → `ChannelListResponse`
- `playlist(id: ID!, part: [String!])` → `Playlist`
- `playlists(ids: [ID!], channelId: ID, mine: Boolean, part: [String!], pageToken: String, maxResults: Int)` → `PlaylistListResponse`
- `playlistItems(playlistId: ID!, part: [String!], pageToken: String, maxResults: Int)` → `PlaylistItemListResponse`
- `search(q: String, type: String, channelId: ID, order: String, publishedAfter: String, publishedBefore: String, regionCode: String, pageToken: String, maxResults: Int, part: [String!])` → `SearchListResponse`
- `comments(id: ID, parentId: ID, part: [String!], pageToken: String, maxResults: Int)` → `CommentListResponse`
- `commentThreads(videoId: ID, channelId: ID, part: [String!], pageToken: String, maxResults: Int)` → `CommentThreadListResponse`
- `subscriptions(mine: Boolean, channelId: ID, part: [String!], pageToken: String, maxResults: Int)` → `SubscriptionListResponse`
- `captions(videoId: ID!, part: [String!])` → `[Caption!]`
- `members(mode: String, part: [String!], pageToken: String, maxResults: Int)` → `MemberListResponse`
- `membershipsLevels(part: [String!])` → `[MembershipLevel!]`
- `liveBroadcasts(broadcastStatus: String, mine: Boolean, part: [String!], pageToken: String, maxResults: Int)` → `LiveBroadcastListResponse`
- `liveStreams(mine: Boolean, part: [String!], pageToken: String, maxResults: Int)` → `LiveStreamListResponse`
- `liveChatMessages(liveChatId: ID!, part: [String!], pageToken: String, maxResults: Int)` → `LiveChatMessageListResponse`
- `i18nLanguages(part: [String!], hl: String)` → `[I18nLanguage!]`
- `i18nRegions(part: [String!], hl: String)` → `[I18nRegion!]`
- `videoCategories(regionCode: String, hl: String, part: [String!])` → `[VideoCategory!]`
- `activities(mine: Boolean, channelId: ID, part: [String!], pageToken: String, maxResults: Int)` → `ActivityListResponse`

## Mutation Patterns

The root `Mutation` type maps to insert, update, and delete operations:

- `insertVideo(snippet: VideoSnippetInput!, status: VideoStatusInput)` → `Video`
- `updateVideo(id: ID!, snippet: VideoSnippetInput, status: VideoStatusInput)` → `Video`
- `deleteVideo(id: ID!)` → `Boolean`
- `rateVideo(id: ID!, rating: String!)` → `Boolean`
- `insertPlaylist(snippet: PlaylistSnippetInput!, status: PlaylistStatusInput)` → `Playlist`
- `updatePlaylist(id: ID!, snippet: PlaylistSnippetInput, status: PlaylistStatusInput)` → `Playlist`
- `deletePlaylist(id: ID!)` → `Boolean`
- `insertPlaylistItem(snippet: PlaylistItemSnippetInput!)` → `PlaylistItem`
- `deletePlaylistItem(id: ID!)` → `Boolean`
- `insertComment(snippet: CommentSnippetInput!)` → `Comment`
- `updateComment(id: ID!, snippet: CommentSnippetInput!)` → `Comment`
- `deleteComment(id: ID!)` → `Boolean`
- `setCommentModerationStatus(id: ID!, moderationStatus: String!, banAuthor: Boolean)` → `Boolean`
- `insertCommentThread(snippet: CommentThreadSnippetInput!)` → `CommentThread`
- `insertSubscription(snippet: SubscriptionSnippetInput!)` → `Subscription`
- `deleteSubscription(id: ID!)` → `Boolean`
- `insertLiveBroadcast(snippet: LiveBroadcastSnippetInput!, status: LiveBroadcastStatusInput!)` → `LiveBroadcast`
- `updateLiveBroadcast(id: ID!, snippet: LiveBroadcastSnippetInput, status: LiveBroadcastStatusInput)` → `LiveBroadcast`
- `transitionLiveBroadcast(id: ID!, broadcastStatus: String!)` → `LiveBroadcast`
- `deleteLiveBroadcast(id: ID!)` → `Boolean`
- `insertLiveStream(snippet: LiveStreamSnippetInput!, cdn: LiveStreamContentDetailsInput!)` → `LiveStream`
- `updateLiveStream(id: ID!, snippet: LiveStreamSnippetInput, cdn: LiveStreamContentDetailsInput)` → `LiveStream`
- `deleteLiveStream(id: ID!)` → `Boolean`
- `insertLiveChatMessage(snippet: LiveChatMessageSnippetInput!)` → `LiveChatMessage`
- `deleteLiveChatMessage(id: ID!)` → `Boolean`
- `insertLiveChatBan(snippet: LiveChatBanSnippetInput!)` → `LiveChatBan`
- `deleteLiveChatBan(id: ID!)` → `Boolean`
- `insertLiveChatModerator(snippet: LiveChatModeratorSnippetInput!)` → `LiveChatModerator`
- `deleteLiveChatModerator(id: ID!)` → `Boolean`
- `uploadCaption(videoId: ID!, snippet: CaptionSnippetInput!)` → `Caption`
- `updateCaption(id: ID!, snippet: CaptionSnippetInput!)` → `Caption`
- `deleteCaption(id: ID!)` → `Boolean`
- `reportVideoAbuse(videoId: ID!, reasonId: String!, secondaryReasonId: String, comments: String)` → `Boolean`
- `uploadChannelBanner(url: String!)` → `ChannelBanner`
- `setChannelWatermark(channelId: ID!, imageUrl: String!, position: String, timing: String)` → `Boolean`
- `unsetChannelWatermark(channelId: ID!)` → `Boolean`
- `uploadThumbnail(videoId: ID!, url: String!)` → `ThumbnailDetails`
