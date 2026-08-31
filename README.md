# three.js 🚀

## 📖 Описание

**three.js** — это популярная кросс-браузерная JavaScript-библиотека и API для создания и отображения анимированной 3D-графики в веб-браузерах. Проект предоставляет мощные инструменты для работы с WebGL, позволяя разработчикам создавать интерактивные 3D-сцены, игры, визуализации данных и другие графические приложения.

## 🛠 Технологический стек

- **Язык**: JavaScript (ES6+)
- **Типизация**: TypeScript (файлы `.d.ts`)
- **Графика**: WebGL, WebXR (VR/AR)
- **Сборка**: Rollup, npm
- **Тестирование**: Puppeteer, Mocha (unit-тесты)
- **Форматы данных**: glTF, OBJ, FBX, COLLADA, STL и другие

## 📦 Установка и запуск

### Установка через npm

```bash
npm install three
```

### Подключение через CDN

```html
<script src="https://cdnjs.cloudflare.com/ajax/libs/three.js/r128/three.min.js"></script>
```

### Локальный запуск проекта

```bash
# Клонирование репозитория
git clone https://github.com/mrdoob/three.js.git
cd three.js

# Установка зависимостей
npm install

# Запуск dev-сервера для примеров
npm start
```

## 💻 Примеры использования

### Базовый пример — создание 3D-сцены

```javascript
import * as THREE from 'three';

// Создание сцены
const scene = new THREE.Scene();
const camera = new THREE.PerspectiveCamera(75, window.innerWidth / window.innerHeight, 0.1, 1000);
const renderer = new THREE.WebGLRenderer();

renderer.setSize(window.innerWidth, window.innerHeight);
document.body.appendChild(renderer.domElement);

// Добавление объекта
const geometry = new THREE.BoxGeometry();
const material = new THREE.MeshBasicMaterial({ color: 0x00ff00 });
const cube = new THREE.Mesh(geometry, material);
scene.add(cube);

camera.position.z = 5;

// Анимация
function animate() {
    requestAnimationFrame(animate);
    cube.rotation.x += 0.01;
    cube.rotation.y += 0.01;
    renderer.render(scene, camera);
}
animate();
```

### Загрузка 3D-модели (glTF)

```javascript
import { GLTFLoader } from 'three/examples/jsm/loaders/GLTFLoader.js';

const loader = new GLTFLoader();
loader.load('model.gltf', (gltf) => {
    scene.add(gltf.scene);
});
```

## 📁 Структура проекта

| Директория | Описание |
|------------|----------|
| `build/` | Собранные файлы библиотеки (three.js, three.min.js, three.module.js) |
| `docs/` | Документация API, руководства и примеры (en/zh) |
| `editor/` | Визуальный редактор для создания 3D-сцен |
| `examples/` | Более 300 примеров использования библиотеки |
| `src/` | Исходный код библиотеки (модульная структура) |
| `test/` | Модульные и e2e-тесты |
| `utils/` | Утилиты для сборки и конвертации моделей |
| `files/` | Статические ресурсы (шрифты, иконки, стили) |

### Ключевые модули `src/`

- **animation/** — система анимации (клипы, микшеры, треки)
- **cameras/** — типы камер (перспективная, ортографическая)
- **core/** — базовые классы (Object3D, BufferGeometry, Raycaster)
- **geometries/** — геометрические примитивы (Box, Sphere, Torus и др.)
- **lights/** — источники света (Ambient, Directional, Point, Spot)
- **loaders/** — загрузчики форматов (glTF, OBJ, FBX и др.)
- **materials/** — материалы (Basic, Lambert, Phong, Standard, Physical)
- **math/** — математические классы (Vector2/3/4, Matrix3/4, Quaternion)
- **objects/** — 3D-объекты (Mesh, Line, Points, Sprite, Group)
- **renderers/** — рендереры (WebGLRenderer, WebGLRenderTarget)
- **textures/** — текстуры (Texture, CubeTexture, VideoTexture)

## 📄 Лицензия

Проект распространяется под лицензией **MIT**. Подробности см. в файле [LICENSE](LICENSE).