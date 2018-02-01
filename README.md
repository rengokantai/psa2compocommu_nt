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
