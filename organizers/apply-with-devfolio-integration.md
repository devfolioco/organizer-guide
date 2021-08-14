# ✅ Apply with Devfolio Integration

### Getting Started

#### Step 1: Add the script

Include the script once, right before the closing &lt;/body&gt; tag.

```markup
<script defer async src="https://apply.devfolio.co/v2/sdk.js"></script>
```

**Usage with React**

If you're using React, load the SDK script dynamically for every page that has the 'Apply with Devfolio' button.

```jsx
React.useEffect(() => {
    const script = document.createElement('script');
    script.src = 'https://apply.devfolio.co/v2/sdk.js';
    script.async = true;
    script.defer = true;
    document.body.appendChild(script);
    return () => {
      document.body.removeChild(script);
    }
}, []);
```

#### Step 2: Specify button element\(s\)

Copy and paste this code where you want the 'Apply with Devfolio' button to appear on your website.

{% hint style="info" %}
Don't forget to replace **YOUR-HACKATHON-SLUG** with your hackathon's actual slug.
{% endhint %}

```markup
<div 
	class="apply-button" 
	data-hackathon-slug="YOUR-HACKATHON-SLUG" 
	data-button-theme="light"
	style="height: 44px; width: 312px"
></div>
```

{% hint style="warning" %}
Even after adding the code, the button **won't be visible** right away. For it to be visible, your hackathon must be verified on Devfolio.
{% endhint %}

### Button Settings

| Name | Description | Value |
| :--- | :--- | :--- |
| data-hackathon-slug | The slug/key of your hackathon. Refer to the [Links Tab](setup/links.md#devfolio-microsite-url) for more details | String |
| data-button-theme | Controls the appearance of the button. Refer to the screenshot below! | "light", "dark", "dark-inverted" |

#### **Customisation via the `data-button-theme` attribute**

![Themes for Apply with Devfolio Button](../.gitbook/assets/image%20%28125%29.png)

{% hint style="danger" %}
As a security measure, we disable the button's functionality over website addresses other than the one you specify in the hackathon's setup.
{% endhint %}

