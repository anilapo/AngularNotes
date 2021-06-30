# View Encapsulation in Angular:
Angular encapsulates the styles, but now you can over ride this encapsulation.
Should import View Encapsulation 
`
import {ViewEncapsulation} from '@angular/core'
`
If  `encapsulation:ViewEncapsulation.None`  then no encapsulation in components
```
@Component({
selector:
tempateUrl:
styleUrls:
encapsulation:ViewEncapsulation.None
})
```

`encapsulation:ViewEncapsulation.Emulated` : by default
 `encapsulation:ViewEncapsulation.Native`
`encapsulation:ViewEncapsulation.ShadowDom` : use the ShadowDom technology