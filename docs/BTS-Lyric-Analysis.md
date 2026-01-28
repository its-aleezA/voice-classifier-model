# 🎵 Dataset Insights & Lyrical Patterns

This report provides a qualitative look at the "Lyrical DNA" found within the dataset used to train the classifier.

## 🔍 Member-Specific Stylistic Markers

Based on the TF-IDF feature importance, the model identifies members using the following key patterns:

### 🎹 The Rap Line (Assertive & Introspective)
* [cite_start]**RM:** Uses high-complexity vocabulary and nature-based metaphors (rain, stars, city, moon)[cite: 190, 192]. His lyrics often involve identity-seeking questions (e.g., "Who am I?").
* [cite_start]**Suga (Agust D):** Characterized by "D-Boy" references, mentions of his hometown (Daegu), and themes of "Billboard," "success," and "thorns"[cite: 567, 568]. 
* [cite_start]**J-Hope:** Features rhythmic onomatopoeia, themes of "hope," "vibe," and references to "Pandora" or "Alice in Wonderland"[cite: 920, 921].

### 🎤 The Vocal Line (Emotional & Atmospheric)
* [cite_start]**Jin:** High frequency of themes involving "sacrifice," "longing," and "staying by one's side"[cite: 1999, 2003]. Frequent use of power-ballad vocabulary (heart, storm, smile).
* [cite_start]**Jimin:** Soft, light-based imagery ("I want you to be your light") and themes of "promises" or "awkwardness"[cite: 1464, 1465].
* [cite_start]**V:** Deeply atmospheric and seasonal imagery (snow, winter, jazz, strumming guitars)[cite: 1754, 32].
* [cite_start]**Jungkook:** Direct emotional storytelling with focus on "stars," "light," and "night after night"[cite: 2407, 2411].

## 📈 Class Distribution (Post-Balancing)

By balancing the classes, we ensured that the model treats a 4-word snippet from **Jimin's** *Promise* with the same weight as a 4-word snippet from **Suga's** *Daechwita*.

## 🛠️ Data Preprocessing Note
We explicitly chose **not** to remove all stop words (like "I," "my," "you"). In solo discographies, the frequency of "I" vs. "You" is a significant stylistic marker:
- **Introspective tracks (RM/Suga)** show higher "I" usage.
- **Dedicated fan-tracks (Jungkook/Jimin)** show higher "You" usage.
