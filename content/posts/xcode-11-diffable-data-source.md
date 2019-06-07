---
title: "Xcode 11 Diffable Data Source"
date: 2019-06-06T21:07:57-06:00
---

In the Xcode 11 Beta I started seeing the following errors:

<!--more-->

```
Imported declaration 'UITableViewDiffableDataSourceCellProvider' could not be mapped to 'UITableViewDiffableDataSourceReference.CellProvider'
Imported declaration 'UICollectionViewDiffableDataSourceCellProvider' could not be mapped to 'UICollectionViewDiffableDataSourceReference.CellProvider'
```

I'm not sure if it's related but it started happening after I built for `macOS` using the new Catalyst feature.

Building for a different simulator made the errors go away. I was building for the 
`iPhone Xs`. It built successfully when I switched to `iPhone Xr` then again when I
switched back to `iPhone Xs`.
