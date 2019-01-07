# psa2compocommu_nt

## 3. Communicating with a Template
### 4 Two-way binding
short way vs long way
```
<input type='text' [(ngModel)]='listFilter'/>
<input type='text' [ngModel]='listFilter' (ngModelChange)='listFilter=$event' />
```
or call a function
```
<input type='text' [ngModel]='listFilter' (ngModelChange)='onFilterChange($event)' />
```
```
onFilterChange(filter:string):void{
  this.listFilter=filter;
  this.performFilter(this.listFilter);
}

performFilter(filterBy?:string):void{
  if(filterBy){
    this.filteredProducts = this.products.filter(product=>product.productName.toLocaleLowerCase().index!=-1;
  }
  else{
    this.filteredProducts=this.products
  }
}
```

### 5 Getters and Setters
```
<input type='text' [(ngModel)]='listFilter'/>
```
```
private _listener: string
get listFilter(): string{
  return this._listFilter;
}
set listFilter(value:string){
  this._listFIlter=value;
  this.performFilter(this.listFilter);
}
```

## 4. ViewChild and ViewChildren
### 3 Demo: ViewChild and Access
```
ngAfterViewInit()
```
so we can get template variable in component after template is rendered

```
@ViewChild('filterElement') filterElementRef:ElementRef;
<input type='text' #filterElement [(ngModel)]='listFilter'/>
```
```
ngAfterViewInit():void{
  console.log(this.filterElementRef);
  this.filterElementRef.nativeElement.focus();
}

```
considerations when using nativeElement
- Using nativeElement -> directly accessing the DOM
- Tightly coupled to the browser
- May not be able to use server side rendering or web workers
- Can pose a security threat, especially if accessing innerHtml


### 4 ViewChildren
```
@ViewChildren('divElementVar')
divElementRefs: QueryList<ElementRef>;
```
Differences:
- Returns a QueryList of element or directive references
- Tracks changes in the DOM
```
this.divElementRefs.changes.subscribe(()=>{})
```

### 4 ViewChildren
Template
```
<input type='text' [(ngModel)]='listFilter'/>
```
Component
```
@ViewChild(NgModel) filterInput: NgModel;
this.filterInput.valueChanges.subscribe(()=>this.performFilter(this.listFilter)):
```

### 5 ViewChild and Angular Forms
Notifying the Component of User Changes
- Two-way binding, the long way
- Getter and setter
- valueChanges observable  

Template-driven | Reactive
---|---
Angular creates the form data structures|We create the form data structures
Based on info in the template|Defined in the component class
Access reference with ViewChild|No need for ViewChild


## 5. Communicating with a Child Component
### 4 Input Property

### 5 Watching for Changes
parentcopmonent->parenttemplate->childcomponent->childtemplate



### 6 Template Reference Variable
(we saw this in ViewChild section)
##### parent Template
```
<pm-criteria #name [dislayDetail]=''>
</pm-criteria>
{{name.listFilter}}
```
##### Child template
```
listFilter:string
```


## 6. ViewChild Decorator
##### parent template
```
<pm-criteria #name [dislayDetail]=''>
</pm-criteria>
```
##### parent component
```
@ViewChild('name')
childcomponent:ChildComponent;
```
