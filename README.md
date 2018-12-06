# spatha.js 🗡

🚧 Status: In Development 🛠️
***
SpathaJS is a simple and tiny utility library for building fast web interfaces, aimed to speed up the first feedbacks from clients, delaying the initially dilemma of *"which technology should I use/or will be mandatory?" 🤔🤓😶

🔧 This micro tool was (inspired) meant to be a JSX-like for UI web platform **prototyping**, avoiding the first battleground with evil stacks and bad configurations that you must learn. Just use what is familiar, the loyal and trusted _cohortes praetorianae_ of Web Development, the eternal Web Standards: vanilla JavaScript, Web APIs, HTML5, CSS3 and the awesome Web Components v1 together.

Using as starting point the [HTML templating implementation](http://exploringjs.com/es6/ch_template-literals.html#sec_html-tag-function-implementation) provided by Dr. Axel Rauschmayer at his book.

```javascript
import { innerHTML, html } from './spatha.mjs';

class MyComponent extends HTMLElement {
  static get observedAttributes() { return ['name']; }
  constructor(...args) {
    super(...args);
  }
  attributeChangedCallback() { this.render(); }
  connectedCallback() { this.render(); }
  showNodeName() {
    alert(this.nodeName);
  }
  render() {
    this[innerHTML] = html`
    <p id onblur='${(e)=>console.log(e.target.textContent)}' class='par' contenteditable>
      <slot name="user-text">ad victoriam!!!!</slot>
    </p>
    <h1 onclick='${this.showNodeName}' style="${{"color": "red", "font-size": "5em"}}">Hello, ${this.getAttribute('name')}</h1>
    `;
  }
}

customElements.define('my-component', MyComponent);

const mc = new MyComponent;
mc.setAttribute('name', 'Maximus');
document.body.appendChild(mc);
```

---

⚠️ Warning: ☢️ not optimized for production ☣️
