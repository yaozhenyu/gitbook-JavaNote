# SpringSecurity

**web配置**

继承WebSecurityConfigurerAdapter

```
@Configuration
@EnableWebSecurity
public class WebSecurityConfig extends WebSecurityConfigurerAdapter {

    @Autowired
    private UserDetailService userDetailService;
    private PasswordEncoder passwordEncoder;

    @Override
    protected void configure(HttpSecurity http) throws Exception {
        http
            .authorizeRequests()
                .antMatchers("/", "/home").permitAll()
                .anyRequest().authenticated()
                .and()
            .formLogin()
                .loginPage("/login")
                .permitAll()
                .and()
            .logout()
                .permitAll();
    }

    @Autowired
    public void configureGlobal(AuthenticationManagerBuilder auth) throws Exception {
        // 用户信息配置在内存中
        auth
            .inMemoryAuthentication()
                .withUser("user").password("password").roles("USER");
        auth.userDetailService(userDetailService).passwordEncoder(passwordEncoder);

    }
}
```



