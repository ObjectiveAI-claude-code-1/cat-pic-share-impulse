# cat-pic-share-impulse

Ranks cat pictures by the strength of the impulse they provoke to share or save. The core question: how strongly would this image compel a viewer to send it to someone else, bookmark it, or return to it — rather than simply smile and scroll past?

## Input

An array of two or more cat pictures (images). Any source, any quality — professional photography and blurry phone snapshots are evaluated with equal seriousness, because shareability does not respect production value.

```json
{
  "type": "array",
  "items": { "type": "image" },
  "minItems": 2
}
```

## Output

An array of numerical scores, one per input image, representing relative share-impulse strength. Higher scores indicate a stronger compulsion to act on the image (share, save, revisit). Scores are normalized and sum to approximately 1, enabling direct comparison and ranking across the input set.

## What It Evaluates

The function measures share impulse along three independent dimensions. Each captures a different facet of the experience that separates a forgettable cat picture from an irresistible one.

### 1. Emotional Immediacy

How fast and how hard does the image hit? This dimension measures the speed and force of the viewer's gut reaction — the involuntary laugh, gasp, or "oh my god" that arrives before conscious thought. The type of emotion does not matter (laughter, tenderness, absurdist delight all qualify); what matters is that the reaction is reflexive and strong. Images that earn a mild, considered "that's nice" score low. Images that strike the viewer like a reflex score high.

### 2. Self-Sufficiency

Can the image travel alone? This dimension measures whether the picture could be dropped into a message thread with no caption, no context, and no explanation and still land with its full impact. The most self-sufficient images are universally legible — any viewer, encountering the image cold, instantly gets it. They do not require knowing the cat, understanding a backstory, or recognizing a meme format. The image is a complete story in a single frame: a gift that unwraps itself.

### 3. Staying Power

Would the image still be just as good on the twentieth viewing? This dimension measures the image's resistance to fading — its ability to remain compelling well beyond the initial encounter. Images with staying power are the ones people save to their camera rolls and keep for months, deploying them at the perfect conversational moment. They have an inexhaustible quality that rewards revisiting. By contrast, images with low staying power are like a joke that is funny exactly once: consumed completely in a single reaction, with no reason to return.

## Use Cases

- **Social media curation**: Selecting the strongest cat pictures for posting from a large pool of candidates.
- **Group chat selection**: Choosing which cat picture to send when you have several good options and want the one most likely to get a reaction.
- **Content platform ranking**: Ordering cat picture feeds or galleries so the most share-worthy images surface first.
- **Personal collection building**: Identifying which images are worth saving for the long term versus which are pleasant but disposable.
- **Understanding virality**: Using cat pictures as a pure test case for what makes visual content travel, free from the confounding effects of controversy, ideology, or outrage.

## How It Works

The function runs three vector completion tasks in parallel, one per evaluation dimension. Each task frames the ranking as a natural conversational scenario where an LLM must choose among the input images:

1. **Emotional Immediacy** — The LLM is asked to select the cat picture that would stop someone mid-scroll, favoring the image with the most visceral, reflexive impact.
2. **Self-Sufficiency** — The LLM is placed in a scenario where it must choose a cat picture to send with absolutely no accompanying text, favoring the image that needs no explanation.
3. **Staying Power** — Through a multi-turn conversation about building a permanent collection, the LLM selects the image most worth keeping forever, favoring the one that resists being used up.

The scores from all three tasks are combined to produce a unified ranking that reflects the full anatomy of the share impulse: images that hit hard, travel light, and last.

## Key Distinctions

This function does **not** evaluate:
- Photographic quality or technical composition
- Breed, cuteness, or aesthetic beauty in the abstract
- How much a viewer *likes* the image

It evaluates **only** the strength of the impulse the image provokes — the line between passive consumption (a brief smile, then gone) and active behavior (sharing, saving, returning). A technically flawed image that provokes an irresistible urge to forward it will outrank a beautifully composed image that inspires nothing more than quiet appreciation.
