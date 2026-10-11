# ManjuForge-Style Story Continuity Skill

This skill turns any AI agent into a serialized anime story engine.
When writing a new episode, the agent MUST follow these rules.

## Memory Files (source of truth)

Before writing any episode, load these files from the repo:

- `story/character_graph.json` — who exists, how they relate
- `story/world_bible.json` — locations, factions, magic rules
- `story/timeline.json` — what happened in every prior episode, in order
- `story/foreshadow.json` — planted clues and their intended payoffs
- `story/episode_index.json` — title, logline, cliffhanger of each episode

If any file is missing, create it with sensible defaults before continuing.

## Rules for Every New Episode

1. Read the last 3 episodes from `timeline.json` first.
2. Advance at least one plot thread from `foreshadow.json`.
3. Plant at least one new clue that will pay off 3+ episodes later.
4. Never contradict established character personality or world rules.
5. End on a cliffhanger that raises a new question the viewer needs answered.
6. Do not resolve the main arc. Each episode should make the overall situation more complicated, not less.
7. Update memory files after writing: append to `timeline.json`, update `foreshadow.json`, add a new entry to `episode_index.json`.

## Episode Output Format

Each episode MUST be produced as a structured JSON file:

```json
{
  "episode_number": 1,
  "title": "",
  "logline": "",
  "cold_open": "30-second hook",
  "acts": [
    {
      "act": 1,
      "duration_seconds": 150,
      "scenes": [
        {
          "scene_id": "1.1",
          "duration_seconds": 8,
          "visual_prompt": "For the video model — describes shot, camera, mood",
          "dialogue": "Character name: line of dialogue",
          "sfx": "optional sound effect note"
        }
      ]
    }
  ],
  "cliffhanger": "",
  "next_episode_teaser": "",
  "foreshadow_planted": [],
  "foreshadow_paid_off": []
}
