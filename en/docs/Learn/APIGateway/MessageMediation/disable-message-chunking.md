# Disable Message Chunking

When processing large messages, message chunking facilitates sending the message as multiple independent chunks. Message chunking is set using the `Transfer-Encoding: chunked` header. However, some legacy backends might not support chunked messages. To disable sending chunked messages to the backend for a specific API, follow the steps below:

1.  Create an `XML` file with the following content:

    **disable chunking**

    ``` xml
        <sequence xmlns="http://ws.apache.org/ns/synapse" name="disableChunkingSeq">
           <property name="DISABLE_CHUNKING" value="true" scope="axis2"/>
        </sequence>
    ```

2.  Use the same sequence and apply it as a mediation extension to the inflow of this particular API. For more details, see [Creating per-API extensions](_Adding_Mediation_Extensions_) . Once the API is published, chunking is disabled for the message that is sent to the backend.

        !!! info
    To stop chunked messages from being sent to the client, you can apply the same mediation extension to the out sequence as well.



