
https://flatpickr.js.org/plugins/
https://github.com/adrienpoly/stimulus-flatpickr

```typescript
// Add to app/javascript/controllers/application.js
import Flatpickr from 'stimulus-flatpickr'
application.register('flatpickr', Flatpickr)
```

Run in terminal
```bash
bin/importmap pin stimulus-flatpickr
bin/importmap pin flatpickr/dist/plugins/monthSelect
```


```bash
bin/rails g stimulus month-flatpickr
```

```typescript
// app/javascript/controllers/month_flatpickr_controller.js
import Flatpickr from 'stimulus-flatpickr'
import monthSelectPlugin from "flatpickr/dist/plugins/monthSelect"

// Connects to data-controller="month-flatpickr"
export default class extends Flatpickr {
  connect() {
    this.config = {
      plugins: [
        new monthSelectPlugin({
          shorthand: true, //defaults to false
          dateFormat: "m.y", //defaults to "F Y"
          altFormat: "F Y", //defaults to "F Y"
          theme: "dark" // defaults to "light"
        })
      ]
    }
    super.connect()
  }
}
```

```Ruby
<%= f.text_field :month, placeholder: 'Select Month',
   data: {
      controller: 'month-flatpickr',
      flatpickr_enable_time: false
   } %>
```

By default the plugin styles aren’t included.
Add this to `app/assets/stylesheets/application.css`
```css
@import url(‘https://cdn.jsdelivr.net/npm/flatpickr@4.6.13/dist/plugins/monthSelect/style.css’)
```