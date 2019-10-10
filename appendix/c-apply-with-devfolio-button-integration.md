# ‘Apply with Devfolio’ button integration

## Prerequisites

* A unique key `myhackathonkey.` This will be provided by the community manager.
* The button requires SSL to be setup on the hackathon website to work as expected. This means the hackathon site should use be on `https`. [This](https://www.digitalocean.com/community/tutorials/how-to-secure-nginx-with-let-s-encrypt-on-ubuntu-16-04) article can be referred for the purpose.

### **The Setup**

* Add a button element in your markup. 

```markup
<button id="devfolio-apply-now"><svg class="logo" xmlns="http://www.w3.org/2000/svg" fill="#fff"
viewBox="0 0 115.46 123.46" style="height:24px;width:24px;margin-right:8px">
<path d="M115.46 68a55.43 55.43 0 0 1-50.85 55.11S28.12 124 16 123a12.6 12.6 0 0 1-10.09-7.5 15.85 15.85 0 0 0 5.36 1.5c4 .34 10.72.51 20.13.51 13.82 0 28.84-.38 29-.38h.26a60.14 60.14 0 0 0 54.72-52.47c.05 1.05.08 2.18.08 3.34z" />
<path d="M110.93 55.87A55.43 55.43 0 0 1 60.08 111s-36.48.92-48.58-.12C5 110.29.15 104.22 0 97.52l.2-83.84C.38 7 5.26.94 11.76.41c12.11-1 48.59.12 48.59.12a55.41 55.41 0 0 1 50.58 55.34z" />
</svg>Apply with Devfolio</button>
```

* Add the below script preferably before the closing body tag.

{% tabs %}
{% tab title="JavaScript" %}
{% code-tabs %}
{% code-tabs-item title="apply-snippet.js" %}
```javascript
document.addEventListener('DOMContentLoaded', function () {
    let devfolioOptions = {
        buttonSelector: '#devf
olio-apply-now',
        key: 'myhackathonkey',
    }

    let script = document.createElement('script');
    script.src = "https://apply.devfolio.co";
    document.head.append(script);

    script.onload = function () {
        new Devfolio(devfolioOptions);
    }

    script.onerror = function () {
        document.querySelector(devfolioOptions.buttonSelector).addEventListener('click', function () {
            window.location.href = 'https://devfolio.co/external-apply/' + devfolioOptions.key;
        });
    }
});
```
{% endcode-tabs-item %}
{% endcode-tabs %}
{% endtab %}

{% tab title="ReactJS" %}
{% code-tabs %}
{% code-tabs-item title="react-apply-snippet.jsx" %}
```jsx
componentDidMount = () => {
  window.onload = this.loadApplyNowScript();
};

loadApplyNowScript = () => {
  const script = document.createElement('script');
  script.src = 'https://apply.devfolio.co';
  script.async = true;
  document.body.appendChild(script);

  script.onload = this.handleLoad;
};

handleLoad = () => {
  new Devfolio({ key: 'myhackathonkey', buttonSelector: '#devfolio-apply-now' });
};
```
{% endcode-tabs-item %}
{% endcode-tabs %}
{% endtab %}
{% endtabs %}

* The CSS below adds a default style to the apply now button. Add the following snippet to  the website’s styles.

{% code-tabs %}
{% code-tabs-item title="apply-snippet.css" %}
```css
#devfolio-apply-now {
    -ms-flex-align: center;
    -webkit-box-align: center;
    align-items: center;
    background-color: #3770FF;
    border-radius: 3px;
    border: none;
    color: #FFFFFF;
    cursor: pointer;
    display: -ms-flexbox;
    display: -webkit-box;
    display: flex;
    font-family: -apple-system, BlinkMacSystemFont, 'Segoe UI', Helvetica, Arial, sans-serif, 'Apple Color Emoji', 'Segoe UI Emoji', 'Segoe UI Symbol';
    font-size: 18px;
    font-weight: 600;
    padding: 12px 20px;
    text-align: center;
    text-transform: lowercase;
}

#devfolio-apply-now:not([disabled]) {
    cursor: pointer;
}

#devfolio-apply-now:hover {
    background-color: #2954BF !important;
}
```
{% endcode-tabs-item %}
{% endcode-tabs %}

## Troubleshooting

#### Error : No 'Access-Control-Allow-Origin' header;

![CORS issue](../.gitbook/assets/image%20%281%29.png)

> If you get the CORS issue in browser ask the organizer to whitelist the hackathon domain.

