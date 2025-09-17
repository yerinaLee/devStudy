주요차이

@Controller : **view를** 반환
@RestController : **data를** 반환(형태 : Json)



@Controller
```
@Target(ElementType.TYPE)  
@Retention(RetentionPolicy.RUNTIME)  
@Documented  
@Component  
public @interface Controller {  
  
   /**  
    * Alias for {@link Component#value}.  
    */   
	@AliasFor(annotation = Component.class)  
    String value() default "";  
  
}
```


@RestController
```
@Target(ElementType.TYPE)  
@Retention(RetentionPolicy.RUNTIME)  
@Documented  
@Controller  
@ResponseBody  
public @interface RestController {  
  
   /**  
    * The value may indicate a suggestion for a logical component name,    
    * to be turned into a Spring bean in case of an autodetected component.    
    * @return the suggested component name, if any (or empty String otherwise)  
    * @since 4.0.1  
    */   
    @AliasFor(annotation = Controller.class)  
    String value() default "";  
  
}
```



RestController는 Controller + ResponseBody를 합한 형태

