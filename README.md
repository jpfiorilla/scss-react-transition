## Easy markup for react-transition-group

For when you don't feel like googling that weird pattern `react-transition-group` and its variants use every dang time.

Handles one or multiple class/id names, timings, and eases.

```scss
@import '../node_modules/scss-react-transition/scss-react-transition.scss';

@include transition('test #test2', (opacity: (0.01, 1), max-height: (0, 30px)), 150 .1s, ease ease-out);
```

yields:

```css
.test-enter, #test2-enter {
  opacity: 0.01;
  max-height: 0;
}

.test-enter.test-enter-active, #test2-enter#test2-enter-active {
  opacity: 1;
  max-height: 30px;
  transition: 150ms ease;
}

.test-exit, .test-leave, #test2-exit, #test2-leave {
  opacity: 1;
  max-height: 30px;
}

.test-exit.test-exit-active, .test-leave.test-leave-active, #test2-exit#test2-exit-active, #test2-leave#test2-leave-active {
  opacity: 0.01;
  max-height: 0;
  transition: 0.1s ease-out;
}
```

(It does both `-exit` and `-leave` for the out transitions because they changed the class names in the React 16 version.)
