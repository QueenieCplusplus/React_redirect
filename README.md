# React_redirect

Let’s now move our attention to admin route. We don’t want use to see Admin component unless they are logged in. In technical terms, we want use to redirect to Login component if loggedIn value somewhere in the application is false. React Router provides Redirect component which redirect user to a URL path. We want user to redirect to /login path unless they are logged in. Let’s create a AppState global variable.


        // application state (index.js)
        const AppState = {
            loggedIn: false,
            login: function(){
                this.loggedIn = true;
            },
            logout: function(){
                this.loggedIn = false;
            }
        };
        const Admin = () => AppState.loggedIn ? 
                            <h1>Admin Component</h1> : 
                            <Redirect to="/login" />;

One thing to remember here is Redirect component will redirect user only in rendering phase which means when component is mounting, React will bootstrap Redirect component and Redirect component will do something in background to navigate user away from current location. Redirect component is not useful when you have to programatically redirect user after component is mounted, that’s where history props comes into play.
You can also see that ADMIN NavLink is not active because we were redirected to /login route (which renders Login component) and there is no NavLink for that. Redirect component’s to prop is used here to tell React Router where to redirect the user. to prop can also be an Object {pathname: ‘/login’, state: {…}} where state is any payload you want to pass to Login component as prop which is accessible from props.location.state inside Login component.

# Ref Doc

https://medium.com/jspoint/basics-of-react-router-v4-336d274fd9e0
