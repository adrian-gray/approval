## Game Sounds

| SFX Name | Version | Implementation |
|---|---|---|
| anticipation.mp3 | | Reel landing anticipation |
| base_bgm_01.mp3 | | 3-5 rows active |
| base_bgm_02.mp3 | | 6-9 rows active |
| base_bgm_03.mp3 | | 10-12 rows active |
| base_bgm_04.mp3 | | 12+ rows active |
| bigwin_1_2.mp3 | | 1 of 2 random big win |
| bigwin_3_4.mp3 | | 1 of 2 random big win |
| button.mp3 | | default button click |
| fs_bgm.mp3 | | free spins background music |
| fs_trigger.mp3 | | free spins trigger music |
| fs_wait.mp3 | | free spins after trigger banner wait |
| gong.mp3 | | play after triggering feature symbol |
| ... | | |

## Feature Trigger Flow
```mermaid
gantt
    dateFormat mm:ss
    axisFormat %M:%S
    section Trigger
      2 triggers land : 00:00, 2s
      Anticipate symbol landing : 5s
      Drum sound : 2s
    section Trigger banner
      Free games won banner : 3s
      Free spins trigger sound : 00:09, 3s
    section Reel unlock
      Reel unlock : 2s
      Reel unlock sound : 00:12, 2s
    section Free games banner
      10 Free Games Banner : 3s
      Free Games Banner sound : 00:14, 3s
```

```mermaid
flowchart TD
  SplashScreen["
  Splash Screen

  loader
  title
  background image
  banners
  logo
  responsive layout
  "]

  BaseScreen["
  Base Game Screen

  background
  background animations
  sound - background music
  symbols
  reels layout
  reels frame
  reels positions
  buttons *
  banners *
  game name / logo
  mechanic logo
  buy feature
  music

  custom mechanics *
  responsive layout
  "]

  IsFeatureTrigger{Feature triggered?}

  FeatureTriggeredFlow["
  Feature Trigger Flow

  x free games banner
  feature trigger effects
  feature trigger sequence
  responsive layout
  "]

  FeatureScreen["
  Feature Screen

  background
  background animations
  symbols
  reels layout
  reels frame
  reels positions
  buttons *
  banners *
  game name / logo
  mechanic logo
  buy feature
  music

  custom mechanics *
  responsive layout
  "]

  IsRetrigger{Retrigger?}

  RetriggerFeatureFlow["
  Retrigger Feature Flow

  Free game banner
  X free games banner
  Feature Trigger Sequence
  responsive layout
  "]

  SplashScreen --> BaseScreen
  BaseScreen --> IsFeatureTrigger
  IsFeatureTrigger{Feature triggered?} -->|No| BaseScreen
  IsFeatureTrigger{Feature triggered?} -->|Yes| FeatureTriggeredFlow
  FeatureTriggeredFlow --> FeatureScreen
  FeatureScreen --> IsRetrigger
  IsRetrigger{Retriggered?} -->|No| BaseScreen
  IsRetrigger{Retriggered?} -->|Yes| RetriggerFeatureFlow
  RetriggerFeatureFlow --> FeatureScreen

```
