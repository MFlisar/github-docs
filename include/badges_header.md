<script src="https://code.jquery.com/jquery-3.7.1.min.js"></script>
<script src="https://cdnjs.cloudflare.com/ajax/libs/moment.js/2.18.1/moment.min.js"></script>
<script>
$.get('https://api.github.com/repos/mflisar/{{ page.meta.library }}/releases/latest', function (data) {
  let date = new Date(data['created_at']);
  let label1 = data['tag_name'];
  document.getElementById("version").innerText = label1;
  let label2 = moment(date).format("DD/MM/YYYY");
  let link1 = "https://img.shields.io/badge/Latest_Release-" + label1 + "-green?style=for-the-badge&amp;labelColor=444444";
  let link2 = "https://img.shields.io/badge/Last_Update-" + label2 + "-green?style=for-the-badge&amp;labelColor=444444";
  document.getElementById("latest-release").src = link1;
  document.getElementById("last-update").src = link2;
 
});
$.get('https://api.github.com/repos/mflisar/{{ page.meta.library }}', function (data) {
  let license = data['license']['name'];
  let link3 = "https://img.shields.io/badge/License-" + license + "-blue?style=for-the-badge&amp;labelColor=444444";
  let stars = data['stargazers_count'];
  let forks = data['forks_count'];
  document.getElementById("stars").innerText = stars;
  document.getElementById("forks").innerText = forks;
  document.getElementById("license").src = link3;
});
</script>

<div>
<a href="https://github.com/MFlisar/{{ page.meta.library }}" target="_blank"><img alt="Github" src="https://img.shields.io/badge/Github-444444?style=for-the-badge&amp;logo=github&amp;logoColor=white"></a>
<a href="https://jitpack.io/#MFlisar/{{ page.meta.library }}" target="_blank"><img alt="Jitpack" src="https://img.shields.io/badge/Jitpack-888888?style=for-the-badge&amp;logo=github&amp;logoColor=white"></a>
</div>
<div>
<!--
<a href="https://github.com/MFlisar/{{ page.meta.library }}" target="_blank"><img alt="Github" src="https://img.shields.io/badge/Github-Open-444444?style=for-the-badge&amp;logo=github&amp;logoColor=white"></a>-->
<a href="https://github.com/MFlisar/{{ page.meta.library }}/releases/latest" target="_blank"><img id="latest-release" alt="Release" src="https://img.shields.io/badge/Latest_Release-_-green?style=for-the-badge&amp;labelColor=444444"></a>
<a href="https://github.com/MFlisar/{{ page.meta.library }}/releases/latest" target="_blank"><img id="last-update" alt="Release" src="https://img.shields.io/badge/Latest_Release-_-green?style=for-the-badge&amp;labelColor=444444"></a>
<a href="https://github.com/MFlisar/{{ page.meta.library }}" target="_blank"><img id="license" alt="License" src="https://img.shields.io/badge/License-_-blue?style=for-the-badge&amp;labelColor=444444"></a>
</div>

:material-tag-outline: <span id="version"></span> :material-star-outline: <span id="stars"></span> :material-source-fork: <span id="forks"></span>