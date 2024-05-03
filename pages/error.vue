<script setup lang="ts">
const goBack = () => {
    window.history.back();
}

</script>

<template>
    <div>
        <div class="container">
            <div class="copy-container center-xy">
                <p>
                    Error pokemon not found.
                </p>
                <br />
                <button @click="goBack">Go back</button>
            </div>
        </div>
    </div>
</template>

<style>

button {
  background-color: #f44336;
  border: none;
  color: white;
  padding: 15px 32px;
  text-align: center;
  text-decoration: none;
  display: inline-block;
  font-size: 16px;
  margin: 4px 2px;
  cursor: pointer;
  transition: background-color 0.3s;
}

button:hover {
  background-color: red;
  transition: background-color 0.3s;
}

.center-xy {
  width: inherit;
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%);
  position: absolute;
}

html,
body {
  font-family: "Roboto Mono", monospace;
  font-size: 16px;
}

html {
  box-sizing: border-box;
  user-select: none;
}


.container {
  width: 100%;
}

.copy-container {
  text-align: center;
}

p {
  color: #fff;
  font-size: 24px;
  letter-spacing: 0.2px;
  margin: 0;
}

#cb-replay {
  fill: #666;
  width: 20px;
  margin: 15px;
  right: 0;
  bottom: 0;
  position: absolute;
  overflow: inherit;
  cursor: pointer;
}

</style>