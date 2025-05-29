<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1">
  <title>Study Material Portal</title>
  <link rel="stylesheet" href="styles.css">
</head>
<body>
  <div class="container">
    <h1>Study Materials by Grade</h1>
    <label for="gradeSelect">Select Grade:</label>
    <select id="gradeSelect" onchange="loadMaterials()">
      <option value="">-- Choose Grade --</option>
      <option value="8">Grade 8</option>
      <option value="9">Grade 9</option>
      <option value="10">Grade 10</option>
      <option value="11">Grade 11</option>
      <option value="12">Grade 12</option>
    </select>

    <div id="materialsContainer" class="materials"></div>
  </div>

  <script src="script.js"></script>
</body>
</html>
body {
  font-family: Arial, sans-serif;
  margin: 0;
  padding: 2rem;
  background-color: #f9f9f9;
}

.container {
  max-width: 800px;
  margin: auto;
  background: white;
  padding: 2rem;
  border-radius: 8px;
  box-shadow: 0 0 10px #ccc;
}

h1 {
  text-align: center;
}

select {
  width: 100%;
  padding: 0.5rem;
  margin-bottom: 1rem;
}

.materials ul {
  list-style-type: none;
  padding: 0;
}

.materials li {
  padding: 0.5rem 0;
}

.materials a {
  text-decoration: none;
  color: #3366cc;
}
const studyMaterials = {
  8: [
    { title: "Maths - Algebra Basics", link: "#" },
    { title: "Science - Cells and Organisms", link: "#" },
    { title: "English - Grammar Practice", link: "#" }
  ],
  9: [
    { title: "Maths - Linear Equations", link: "#" },
    { title: "Science - Laws of Motion", link: "#" },
    { title: "English - Essay Writing", link: "#" }
  ],
  10: [
    { title: "Maths - Trigonometry", link: "#" },
    { title: "Science - Electricity", link: "#" },
    { title: "English - Reading Comprehension", link: "#" }
  ],
  11: [
    { title: "Maths - Calculus Intro", link: "#" },
    { title: "Physics - Kinematics", link: "#" },
    { title: "Biology - Cell Division", link: "#" }
  ],
  12: [
    { title: "Maths - Integrals", link: "#" },
    { title: "Chemistry - Organic Compounds", link: "#" },
    { title: "English - Literature Review", link: "#" }
  ]
};

function loadMaterials() {
  const grade = document.getElementById("gradeSelect").value;
  const container = document.getElementById("materialsContainer");
  container.innerHTML = "";

  if (grade && studyMaterials[grade]) {
    const list = document.createElement("ul");
    studyMaterials[grade].forEach(item => {
      const li = document.createElement("li");
      li.innerHTML = `<a href="${item.link}" target="_blank">${item.title}</a>`;
      list.appendChild(li);
    });
    container.appendChild(list);
  } else {
    container.innerHTML = "<p>Please select a grade to see the materials.</p>";
  }
}
