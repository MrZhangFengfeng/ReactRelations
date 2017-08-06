### 正常

    return(
      <div>
        <ul>
          {
            this.state.repos.map((repo,index)=>{
              const to = 'repo/${repo.userName}/${repo.repoName}';
              return(
                <li key={index}>
                  <Link to={to} activeClassName='active'>{repo.repoName}</Link>
                </li>
              )
            })
          }
        </ul>
      </div>
    )
    
### 优化

    <NavLink to={to} >{repo.repoName}</NavLink>

    function NavLink(props){
      return <Link activeClassName = 'active' {...props}></Link>
    }
    
    export default NavLink;
