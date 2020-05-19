# express te next ile hata fırlatma

express modulunde api.js de bulunan handlerdeki res.render kısmını res.json ile değiştirince her hangi bir yapıdan next ile fırlattığımız hataları yakalayabiliyoruz

```javascript
// error handler api.js
app.use((err, req, res, next) => {
  // set locals, only providing error in development
  res.locals.message = err.message;
  res.locals.error = req.app.get('env') === 'development' ? err : {};

  // render the error page
  res.status(err.status || 500);
  res.json({error: res.locals.error});
});

module.exports = app;
```

hata fırlatma
```javascript
next({message: "hata kanka", code: 15});
```

ekran görüntüsü
```javascript
{
    "message": "hata kanka",
    "code": 15
}
```
