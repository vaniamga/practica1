
fetch('https://raw.githubusercontent.com/vaniamga/api/main/json/personas.json')
  .then((res) => res.json())
  .then((data) => posts.value = data)
  .catch((e) => console.log (e))
  .finally(() => {

  }