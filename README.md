# Quests

<!-- Save this as quest.html and host on GitHub Pages or any web host -->

<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8" />
<title>Your Quest</title>
<style>
  body { font-family: 'Georgia', serif; background: #111; color: #eee; text-align:center; padding: 2rem;}
  .quest-box { border: 2px solid #6a0dad; padding: 1.5rem; border-radius: 10px; background: #222; display: inline-block; }
</style>
</head>
<body>

<h1>Your Quest Awaits</h1>
<div class="quest-box" id="questBox">
  Loading your quest...
</div>

<script>
  // List of quest words (you can add more)
  const questWords = ["dragon", "shadow", "ember", "forge", "sorcery", "blade", "cloak", "potion", "quest", "realm"];

  // Get username from URL param
  const urlParams = new URLSearchParams(window.location.search);
  const user = urlParams.get('user') || "Adventurer";

  // Pick a quest word based on username hash (to keep consistent for each user)
  function hashCode(str) {
    let hash = 0;
    for(let i=0; i<str.length; i++) {
      hash = str.charCodeAt(i) + ((hash << 5) - hash);
      hash = hash & hash; // Convert to 32bit integer
    }
    return Math.abs(hash);
  }

  const index = hashCode(user) % questWords.length;
  const questWord = questWords[index];

  // Show the quest
  const questBox = document.getElementById("questBox");
  questBox.innerHTML = `<p>Make the streamer say the word <strong>"${questWord}"</strong>.</p><p>Good luck, ${user}!</p>`;
</script>

</body>
</html>
