# psa2compocommu_nt


short way vs long way
```
<input type='text' [(ngModel)]='listFilter'/>
<input type='text' [ngModel]='listFilter' (ngModelChange)='listFilter=$event' />
```
