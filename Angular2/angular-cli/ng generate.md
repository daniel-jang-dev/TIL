		ng generate component my-new-component
		ng g component my-new-component # using the alias

components support relative path generation
if in the directory src/app/feature/ and you run

		ng g component new-cmp

your component will be generated in src/app/feature/new-cmp
but if you were to run

    ng g component ../newer-cmp

your component will be generated in src/app/newer-cmp
