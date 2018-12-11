---
layout: post
title: '[Codility] Encryptor'
excerpt: 
category: Algorithm
tags:
  - Algorithm
  - Codility
  - Encryptor
---

```js
// 원판 암호기의 바깥쪽 원판에 적힐 문자 결정

function Encryptor() {
    let obj = {}
    let extraCharactors = [" ",".","?","!","%","#","'","&","$","@",":","/"];
    // 특수문자 추가
    let N_ALPHABET = 26;
    // 알파벳 갯수
    obj.chars = [];
    // 바깥쪽 원판의 문자집합은 chars 프로퍼티에 배열로 저장

    //원판배열에 소문자,대문자 추가
    for(let b='a'.charCodeAt(0);b<='z'.charCodeAt(0);b++) {
        obj.chars.push(String.fromCharCode(b));
    }
    for(let c='A'.charCodeAt(0);c<='Z'.charCodeAt(0);c++) {
        obj.chars.push(String.fromCharCode(c));
    }
    //숫자 추가
    for(let d=0;d<=9;d++) {
        obj.chars.push(d.toString())
    }    
    //특수문자 추가
    for(let j=0;j<extraCharactors.length;j++) {
        obj.chars.push(extraCharactors[j]);
    }

    //chars 배열의 길이
    obj.nchars = obj.chars.length;

    obj.numberOf = function(ch) {
        let code = ch.charCodeAt(0);
        if(code>='a'.charCodeAt(0) && code<='z'.charCodeAt(0)) {
            return code - 'a'.charCodeAt(0);
        } else if(code>='A'.charCodeAt(0) && code<='Z'.charCodeAt(0)) {
            return N_ALPHABET + code - 'A'.charCodeAt(0);
        } else if(code>='0'.charCodeAt(0) && code<='9'.charCodeAt(0)) {
            return 2*N_ALPHABET + code - '0'.charCodeAt(0);
        } else {
            for(let f=0;f<extraCharactors.length;f++) {
                if( ch == extraCharactors[f]) {
                    return 2*N_ALPHABET + 10 + f;
                }
            }
            return null;
        }
    }
}    

```