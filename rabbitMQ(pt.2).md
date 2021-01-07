
1. pom.xml

        <dependency>
            <groupId>org.springframework.boot</groupId>
            <artifactId>spring-boot-starter-amqp</artifactId>
        </dependency>

2. application.properties

2. DTO

@Component
public class MessageSender {

    private RabbitTemplate rabbitTemplate;
    private Queue messageQueue;

    @Autowired
    public void setRabbitTemplate(RabbitTemplate rabbitTemplate) {
        this.rabbitTemplate = rabbitTemplate;
    }

    @Autowired
    public void setMessageQueue(Queue messageQueue) {
        this.messageQueue = messageQueue;
    }

    public void sendMessage(Message message) {
        this.rabbitTemplate.convertAndSend(this.messageQueue.getName(), message);
    }
}

        
3. Controller

@RestController
@RequestMapping(value = "/messages")
public class MessageController {

    private MessageService messageService;

    @Autowired
    public void setMessageService(MessageService messageService) {
        this.messageService = messageService;
    }

    @GetMapping(value = "")
    @ResponseBody
    public Boolean sendMessage() throws InterruptedException {
        return messageService.sendMessage();
    }
}
