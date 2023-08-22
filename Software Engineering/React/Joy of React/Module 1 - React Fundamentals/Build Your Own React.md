```js
function render(reactElement, containerDOMElement) {
  const element = document.createElement(reactElement.type);

  for (const prop in reactElement.props) {
    element.setAttribute(prop, reactElement.props[prop])
  }

  element.innerText = reactElement.children

  containerDOMElement.appendChild(element)

}

const reactElement = {
  type: 'button',
  props: {
    href: 'https://wikipedia.org/',
  },
  children: 'Read more on Wikipedia',
};

const containerDOMElement =
  document.querySelector('#root');

render(reactElement, containerDOMElement);

