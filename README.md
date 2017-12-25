# Async EventsEmitter

Fork from [offical events module](https://github.com/nodejs/node/blob/master/lib/events.js)

## Async

change normal events by using async handler.

## Example

**Sourtce Code:**

```javascript
const a = new EventEmitter();
a.on('aaa', async () => {
    console.log('start:', '1 = ', 'aaa', '->', new Date().getTime());
    await new Promise(resolve => setTimeout(resolve, 3000));
    console.log('end:', '1 = ', 'aaa', '->', new Date().getTime());
});
a.on('aaa', async () => {
    console.log('start:', '2 = ', 'aaa', '->', new Date().getTime());
    await new Promise(resolve => setTimeout(resolve, 3000));
    console.log('end:', '2 = ', 'aaa', '->', new Date().getTime());
});
a.on('aaa', async () => {
    console.log('start:', '3 = ', 'aaa', '->', new Date().getTime());
    await new Promise(resolve => setTimeout(resolve, 3000));
    console.log('end:', '3 = ', 'aaa', '->', new Date().getTime());
});
 
(async () => {
    await a.emit('aaa');
    console.log('all done');
})();
```

**Output:**

```bash
/**
 * @output:
 * start: 1 =  aaa -> 1487673861652
 * end: 1 =  aaa -> 1487673864656
 * start: 2 =  aaa -> 1487673864657
 * end: 2 =  aaa -> 1487673867663
 * start: 3 =  aaa -> 1487673867663
 * end: 3 =  aaa -> 1487673870664
 * all done
 *
 */
```