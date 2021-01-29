---
title: Tow Request Methods Of Antd ProTable
layout: blog.njk
date: 2021-01-30
tags: blog
categories:
  - Antd
---

## 方法一
```javascript
request={async (
        // 第一个参数 params 查询表单和 params 参数的结合
        // 第一个参数中一定会有 pageSize 和  current ，这两个参数是 antd 的规范
        params: T & {
          pageSize: number;
          current: number;
        },
        sort,
        filter,
      ) => {
        // 这里需要返回一个 Promise,在返回之前你可以进行数据转化
        // 如果需要转化参数可以在这里进行修改
        const msg = await queryRule({
          currentPage: params.current,
          numPerPage: params.pageSize,
        });
        return {
          data: msg.data.recordList,
          // success 请返回 true，
          // 不然 table 会停止解析数据，即使有数据
          success: msg.errorCode === 0,
          // 不传会使用 data 的长度，如果是分页一定要传
          // total: msg.data.pagination.totalCount,
        };
      }}
```

## 方法二
```javascript
request={async (params, sorter, filter) => {
  const msg = await queryRule({ ...params, sorter, filter });
  return {
    data: msg.data.recordList,
    success: msg.errorCode === 0,
  };
}}
```

## 方法三
```javascript
request={(params) =>
  queryRule(params).then((res) => {
    const result = {
      data: res.data.recordList,
      total: res.data.totalCount,
      success: res.errorCode === 0,
      pageSize: 10,
      current: res.data.currentPage,
    };
    return result;
  })
}
```