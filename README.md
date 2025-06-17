# vegan-prompt-generator
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Vegan Prompt Generator</title>
  <script>
    function generatePrompt() {
      const mealType = document.getElementById("mealType").value;
      const calories = document.getElementById("calories").value;
      const protein = document.getElementById("protein").value;
      const carbs = document.getElementById("carbs").value;
      const fat = document.getElementById("fat").value;
      const ingredients = document.getElementById("ingredients").value;
      const allergy = document.getElementById("allergy").value;
      const cuisine = document.getElementById("cuisine").value;

      let prompt = `Create a vegan ${mealType} recipe`;
      if (cuisine) prompt += ` inspired by ${cuisine} cuisine`;
      if (calories || protein || carbs || fat) {
        prompt += ` that has approximately`;
        if (calories) prompt += ` ${calories} calories,`;
        if (protein) prompt += ` ${protein}g of protein,`;
        if (carbs) prompt += ` ${carbs}g of carbs,`;
        if (fat) prompt += ` ${fat}g of fat,`;
        prompt = prompt.replace(/,+$/, ''); // Remove trailing comma
      }
      if (ingredients) prompt += `. Use these ingredients if possible: ${ingredients}`;
      if (allergy) prompt += `. Avoid these due to allergies: ${allergy}`;
      prompt += `. Include a full recipe with ingredients, steps, and a nutritional breakdown.`;

      document.getElementById("output").value = prompt;
    }
  </script>
  <style>
    body { font-family: Arial, sans-serif; padding: 2rem; background: #f0f4f8; }
    label { font-weight: bold; }
    input, textarea, select, button {
      display: block; width: 100%; margin: 0.5rem 0 1rem; padding: 0.5rem;
    }
    button { background: #4caf50; color: white; border: none; cursor: pointer; }
    button:hover { background: #45a049; }
    textarea { height: 150px; }
  </style>
</head>
<body>
  <h1>Vegan AI Prompt Generator</h1>
  <label for="mealType">Meal Type</label>
  <input type="text" id="mealType" placeholder="e.g. dinner, lunch, snack">

  <label for="calories">Calories</label>
  <input type="number" id="calories" placeholder="e.g. 500">

  <label for="protein">Protein (g)</label>
  <input type="number" id="protein" placeholder="e.g. 30">

  <label for="carbs">Carbs (g)</label>
  <input type="number" id="carbs" placeholder="e.g. 50">

  <label for="fat">Fat (g)</label>
  <input type="number" id="fat" placeholder="e.g. 15">

  <label for="ingredients">Preferred Ingredients</label>
  <input type="text" id="ingredients" placeholder="e.g. chickpeas, spinach">

  <label for="allergy">Ingredients to Avoid (Allergies)</label>
  <input type="text" id="allergy" placeholder="e.g. soy, nuts">

  <label for="cuisine">Cuisine Type</label>
  <input type="text" id="cuisine" placeholder="e.g. Indian, Mediterranean">

  <button onclick="generatePrompt()">Generate Prompt</button>

  <label for="output">Generated Prompt</label>
  <textarea id="output" readonly></textarea>
</body>
</html>
