# psa2compocommu_nt


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
