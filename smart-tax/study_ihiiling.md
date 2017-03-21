## TranslateService

import: Inectable, Kr, Er, LocalStorageService

private localeResource, locale

constructor(en, kr)
- this.localeResource = {en: en, kr: kr};

setLocale(locale)
- this.locale
- LocalStorageService.set(locale)

getLocale()
- this.locale 이 없으면
  LocalStorageService 의 locale 을 가져옴
  가져올 게 없으면
  setLocale('en')

translate(key)
- this.localeResource[this.getLocale()][key]

## TranslateServicePipe implements PipeTransform

import Pipe, PipeTransform, TranslateService

constructor(translateService: TranslateService)

transform(value, args)
- return this.translateService.translate(value);

## En, Kr 

string values in Korean and English

## module LocalStorageService (object 없이 이용)

var storage: Storage;
1순위 local storage
2순위 session storage
3순위 MemoryStorage

class MemoryStorage {
    private items;
    public getItem(key);
    public removeItem(key);
    public setItem(key, data);
} // 3순위

initStorage()

setItem(name, value)
getItem(name)
removeItem(name)

export function set(name, value)
export function getString(name)
export function getObject<T>(name)
export function remove(name)

## AuthGuardService implements CanActivate

import Injectable, CanActivate, Router, Observable, ApiService

constructor(apiService, router)

canActivate()
- isLoggedIn 이 아니면 /login 으로 이동

