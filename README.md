# [hfm](https://github.com/derekmarcotte/hfm) (High Frequency Monitor) ![hfm mascot](doc/hfm-mascot.png)

hfm is an application to run tests in parallel at a high frequency. If the
outcome of the test results in a state change, other commands can be executed.

```Nginx
global
group {
	test {
	}
}
```

A test could reside at any level of nesting, each is valid:

```Nginx
test="true"
```
```Nginx
test1 {
	test="true"
}
```
```Nginx
group1 {
	test1 {
		test="true"
	}
}
```

If a test is found at a depth, no child configurations are traversed:

	group1 {
		test="true"
		test1 {
			test="won't get here"
		}
	}

