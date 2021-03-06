﻿## useContext

> Make variables global so don't have to drill.

Lets you subscribe to React context without nesting.

	const LocaleContext = React.createContext();
	
	function LocaleProvider({children}) {
	  const thingsToShare = { name: 'Jamie', setName: () => {}, ...};
	  
	  return (
	    <LocaleContext.Provider value={thingsToShare}>
	      {children}
	    </LocaleContext.Provider>
	  );
	}
	
	function Header() {
	  const context = useContext(LocaleContext);
	  return <h1>Hello, {context.name}</h1>;
	}
	
    function App() {
	  return (
	    <LocaleProvider>
	      <Header />
	    </LocaleProvider>
	  );
     }

Kent Dodds implied this isn't the best use of context; its best use would be for sharing data between the parent `<Tabs>` component and the child `<Tab>` components in a library.

